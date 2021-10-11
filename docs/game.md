 # Game API

 - [Get Game List](#get-game-list)
 - [Launch Game](#launch-game)
 - Get Game History
 - Get Game Record

 ## Get Game List

To get list of availiable game to lauch

**Game Object**

| Name     |  Type  | Description                                                 |
| :------- | :----: | :---------------------------------------------------------- |
| gameID   | string | a unique game identifier                                    |
| name     | string | name of game                                                |
| device   |  int   | 1 is only desktop, 2 only mobile, 3 both mobile and desktop |
| category | string | eg.: slot, casual, livedealer                               |
| imageURL | string | URL of game's image                                         |
| provider | string | name of game's provider                                     |

 ```HTTP
 GET: /api/v1/games
 ```

**Example Request**

```HTTP
http://{endpoint}/api/vi/games
```

**Exmple Response**

```json
{
    "games": [
        {
            "gameID": "1001",
            "name": "Girls with Guns II- Frozen Dawn  ",
            "category": "slot",
            "device": 1,
            "imageURL": "/assets/img/game/Feature Slot/GirlsWithGuns_FrozenDawn.jpg",
            "provider": "microgaming"
        },
        {
            "gameID": "1002",
            "name": "High Society ",
            "category": "slot",
            "device": 3,
            "imageURL": "/assets/img/game/Video Slot/High-Society.jpg",
            "provider": "microgaming"
        },
        {
            "gameID": "1003",
            "name": "300 Shields",
            "category": "slot",
            "device": 1,
            "imageURL": "/assets/img/game/Video Slot/300shields.jpg",
            "provider": "microgaming"
        }
    ]
}
```

## Launch Game

**List of availiable game for UAT environment**

| Provider    | Category   | Real  | Demo  |
| :---------- | :--------- | :---: | :---: |
| microgaming | slot       |   ✖   |   ✔   |
| ^           | casual     |   ✖   |   ✔   |
| ^           | livedealer |   ✖   |   ✖   |
| aristocrat  | slot       |   ✔   |   ✔   |
| dragoonsoft | casual     |   ✔   |   ✔   |


```HTTP
POST /api/v1/games
```

**Post Body**

| Name     |  Type  | Required | Remark                            |
| :------- | :----: | :------: | :-------------------------------- |
| gameID   | string |   yes    | -                                 |
| playerID |  int   |   yes    | -                                 |
| device   |  int   |   yes    | 1 is desktop, 2 is moblie         |
| token    | string |   yes    | `uuid` for launch game            |
| lang     | string |    no    | available th and en. default `en` |

**Example Request**

```json
{
	"playerID" : 34696,
	"gameID": "1472",
	"device": "1",
	"demo": false,
	"token": "1680c632-dde3-11e9-8a34-2a2ae2dbcce4"
}
```

**Example Response**

```json
{
    "url": "<launch url"
}
```

## Get Game History

**Example Request**

```HTTP
GET http://endpoint/api/v1/games/history?date=2021-09-20T15:04:05Z&playerID=34689
```
**Exmple Response**

```json
{
    "games": [
        {
            "gameID": "1001",
            "name": "Girls with Guns II- Frozen Dawn  ",
            "category": "slot",
            "device": 1,
            "imageURL": "/assets/img/game/Feature Slot/GirlsWithGuns_FrozenDawn.jpg",
            "provider": "microgaming"
        },
        {
            "gameID": "1002",
            "name": "High Society ",
            "category": "slot",
            "device": 3,
            "imageURL": "/assets/img/game/Video Slot/High-Society.jpg",
            "provider": "microgaming"
        },
        {
            "gameID": "1003",
            "name": "300 Shields",
            "category": "slot",
            "device": 1,
            "imageURL": "/assets/img/game/Video Slot/300shields.jpg",
            "provider": "microgaming"
        }
  ]
}
```


## Get Game Record

TODO..
