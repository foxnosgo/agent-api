# Wallet API

Number of balance and amount must be non-decimal number by using amount * 100, for example

| Actual Amount | In request and response body |
| :-----------: | ---------------------------: |
| 0.20 | 20 |
| 10 | 1000|
| 1,000 | 100000 |
| 32.65 | 3265 |

- [Get Player's Balance](#get-players-balance)
- [Topup](#topup)
- [Withdraw](#withdraw)
- [Transaction History](#transaction-history)

## Get Player's Balance

```HTTP
GET /api/vi/balance/{playerID}
```

**Example Request**

```HTTP
http://endpoint/api/v1/balance/3240
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
POST /api/v1/topup/{playerID}
```

**Posy Body**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| amount | int64 | Yes | must be positive number  |
| wallet | string | No | todo, can be empty |

**Example Request**

```HTTP
http://endpoint/api/v1/topup/3240
```

```json
{
  "amount": 100000, #actual amount is 1,000.00
}
```

**Response Body**

| Name | Type | Description |
| :----- | :-----: | :----- |
| playerID | int | an unique id for player |
| balance | int64 | current balance after topuped |
| wallet | string | wallet's name: casino, sport |
| trxID | int | reference transction id from API system |

**Example Response**

```json
{
  "playerID": 3240,
  "balance": 105000, #Represent: 1,050.00
  "wallet": "casino",
  "trxID": 3521145
}
```

## Withdraw

```HTTP
POST /api/v1/withdraw/{playerID}
```


**Posy Body**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| amount | int64 | Yes | must be positive number |
| wallet | string | No | todo, can be empty |

**Example Request**

```HTTP
http://endpoint/api/v1/withdraw/{playerID}
```

```json
{
  "amount": 100000, #actual amount is 1,000.00
}
```

**Response Body**

| Name | Type | Description |
| :----- | :-----: | :----- |
| playerID | int | an unique id for player |
| balance | int64 | current balance after withdrawal |
| wallet | string | wallet's name: casino, sport |
| trxID | int | reference transction id from API system |

**Example Response**

```json
{
  "playerID": 3240,
  "balance": 5000, #Represent: 50.00
  "wallet": "casino",
  "trxID": 3521146
}
```

## Transaction History

TODO