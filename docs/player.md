# Player API

- [Create Player](#create-player)
- [Get Player List](#get-player-list)
- [Get Player Info](#get-player)

## Create Player

```HTTP
POST: /api/v1/player
```

**Body**

```json
{
  "username": "mycustomer"
}
```

**Example Response**

```json
{
  "player": {
    "id": 3240,
    "username": "mycustomer",
    "balance": 0,
    "status": "active",
    "agentID": 3002
  }
}
```

## Get Player List

```HTTP
GET: /api/v1/player
```

**Parameters**

| Name | Type | Required | Remark |
| :----- | :-----: | :-----: | :----- |
| page | int | No | |
| pageSize | int | No | |

**Example Request**

```HTTP
http://{endpoint}/api/vi/player?page=1&pageSize=50
```

**Exmple Response**

```json
{
  "page": 1,
  "pageSize": 50,
  "total": 1,
  "players": [{
    "id": 3240,
    "username": "mycustomer",
    "balance": 0,
    "status": "active",
    "agentID": 3002
  }]
}
```

## Get Player

```HTTP
GET: /api/v1/player/{playerID}
```

**Example Request**

```HTTP
http://{endpoint}/api/vi/player/mycustomer
```

**Example Response**

```json
{
  "player": {
    "id": 3240,
    "username": "mycustomer",
    "balance": 0,
    "status": "active",
    "agentID": 3002
  }
}
```