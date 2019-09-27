# Wallet API

Number of balance and amount must be non-decimal number by using amount * 100, for example

| Actual Amount | In request and response body |
| :-----------: | ---------------------------: |
| 0.20 | 20 |
| 10 | 1000|
| 1,000 | 100000 |
| 32.65 | 3265 |

- [Wallet API](#wallet-api)
  - [Time Format](#time-format)
  - [Get Player's Balance](#get-players-balance)
  - [Topup](#topup)
  - [Withdraw](#withdraw)
  - [Transaction History](#transaction-history)

## Time Format

The parameter type `datetime` must be used in format `RFC3339` for example.

```json
  {
    "time": "2019-09-23T09:25:35Z07:00"
  }
```
this represent time at `2019/09/23 09:25:35` in location timezone `UTC+7`

*Note*
```
All responses will return time in `UTC`
```

## Get Player's Balance

```HTTP
GET /api/vi/wallet/balance/{playerID}
```

**Example Request**

```HTTP
http://endpoint/api/v1/wallet/balance/3240
```

**Example Response**

```json
{
  "playerID": 3240,
  "balance": 1000
}
```

## Topup

```HTTP
POST /api/v1/wallet/topup/{playerID}
```

**Post Body**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| uuid | string | Yes | to make a transaction unique |
| amount | int64 | Yes | must be positive number  |
| wallet | string | No | todo, can be empty |

**Example Request**

```HTTP
http://endpoint/api/v1/wallet/topup/3240
```

```json
{
  "uuid": "23e4567-e89b-12d3-a456-426655440000",
  "amount": 100000,
}
```

*actual amount is 1,000.00*

**Response Body**

| Name | Type | Description |
| :----- | :-----: | :----- |
| playerID | int | an unique id for player |
| balance | int64 | current balance after topuped |
| wallet | string | wallet's name: casino, sport |
| currentCredit | int | remaining credit |
| trxID | int | reference transction id from API system |
| uuid | string | to make a transaction unique |

**Example Response**

```json
{
  "playerID": 3240,
  "balance": 105000,
  "wallet": "casino",
  "currentCredit": "9888900",
  "trxID": 3521145,
  "uuid": "23e4567-e89b-12d3-a456-426655440000"
}
```

*actual balance: 1,050.00*

## Withdraw

```HTTP
POST /api/v1/wallet/withdraw/{playerID}
```


**Post Body**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| uuid | string | Yes | to make a transaction unique |
| amount | int64 | Yes | must be positive number |
| wallet | string | No | todo, can be empty |

**Example Request**

```HTTP
http://endpoint/api/v1/wallet/withdraw/{playerID}
```

```json
{
  "uuid": "23e4567-e89b-12d3-a456-426655440000",
  "amount": 100000,
}
```

*actual amount is 1,000.00*

**Response Body**

| Name | Type | Description |
| :----- | :-----: | :----- |
| playerID | int | an unique id for player |
| balance | int64 | current balance after withdrawal |
| wallet | string | wallet's name: casino, sport |
| currentCredit | int | remaining credit |
| trxID | int | reference transction id from API system |
| uuid | string | to make a transaction unique |

**Example Response**

```json
{
  "playerID": 3240,
  "balance": 5000,
  "wallet": "casino",
  "currentCredit": "9888900",
  "trxID": 3521146,
  "uuid": "23e4567-e89b-12d3-a456-426655440000"
}
```

*actual amount is 50.00*

## Transaction History

Transaction histoy can be filtered by `playerID` or `type`

```HTTP
GET /api/v1/wallet/history
```

**Parameters**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| from | datetime | Yes | `RFC3339` format |
| to | datetime | No | the end time of filter, `RFC3339` format |
| playerID | int | No |  |
| type | string | No | type of transaction: `deposit`, `withdraw` only |


**Example Request**

```HTTP
http://endpoint/api/v1/wallet/histroy?from=2019-09-23T16%3A19%3A00%2B07%3A00&playerID=34688
```

**Example Response**

```json
{
    "transactions": [
        {
            "trxID": "1848876514",
            "playerID": 34688,
            "time": "2019-09-23T09:19:49Z",
            "type": "deposit",
            "amount": "1000"
        },
        {
            "trxID": "1848876515",
            "playerID": 34688,
            "time": "2019-09-23T09:25:35Z",
            "type": "withdraw",
            "amount": "500000"
        }
    ]
}
```