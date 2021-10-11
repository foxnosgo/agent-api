# GoldenSlot API

- [Player API](docs/player.md)
  - [Create Player](docs/player.md#create-player)
  - [Get Player List](docs/player.md#get-player-list)
  - [Get Player Info](docs/player.md#get-player)
- [Wallet API](docs/wallet.md)
  - [Get Player's Balance](docs/wallet.md#get-players-balance)
  - [Topup](docs/wallet.md#topup)
  - [Withdraw](docs/wallet.md#withdraw)
  - [Transaction History](docs/wallet.md#transaction-history)
- Game API
  - [Get Game List](docs/game.md#get-game-list)
  - [Launch Game](docs/game.md#launch-game)
  - [Get Game History](docs/game.md#get-game-history)

## Request Authentication

All requests must contain `Authorization` with token that provided by GoldenSlot

**Example**

```HTTP
POST /api/v1/player 

Content-Type: application/json
Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6NTA1LCJpYXQiOjE1NjY4ODE5MDV9.SJyXtYiOBgqLHv_ZW0h1M7Kegn8rep4ttfFt8M_mJgIFKmSrBI8SPBG9JZUIJluUReqL7j_80-za5Bw0jkiSA4LdgzFkzSdodIk_e2kjjTzahGSVDwPGMFGo5yE5DyxJZEkkUWXRIZ-rBog8_1ojiBk-ZjOB_LvcASnDMVHfPmYjJxVM4gbbUuvBh4xPaiROtVwSBdKdRKPkDWFN174rNzxfEbYzxn1uE85k9VKih-xOMDFS7EFHBtcsdiQxSZECIfngLiWLhP9Bxw7umIctvPYNieGIhJL-KTuLymioRt63ug5yRAYUJDRB-9wtAspuxhBQyfiu19D61l0cPmJmdCfikaSJXx_yq7dTze_5E8aDkae9gS9MnvCY_k4Ke6pLu5OOJidKnG9yzJ3pXB_28qfVoLoc0LdpcbWJ-lt3gNmJPIofw4qNrgBDjn4r1d1NgG7io70kG-eXxgNRyyr-8Gzr98if4UGw6IrufeqUtgv-uIvFq7fGVNjsrvLa4UL8_7DXd11hVvRvaOGv541Uf-IbpoO2DUdAYqVCr-mcnYdW8HvRKnX31pybpQPRGo7gsaDoPZM9fhCAEHJ4IpSFOly04nfv810pB6YqC9ewmBw4Gs-GDmKZEDgmGzuStnMgBfeRrevLYpI1wBUWt-UPEnNPVfRy97d20Ed5uO6REn8


{
  "username": "testuser"
}

```

## Status code for responses

| Status Code | Description |
| :---------: | :---------- |
| 200 | Success |
| 400 | Invalid agrument |
| 401 | Unauthorize token |
| 403 | Permission denied |
| 409 | Already exists |
| 500 | Internal error from API |

**Example Error Response**

```json
{
    "error": "Request unauthenticated with bearer",
    "message": "Request unauthenticated with bearer",
    "code": 16,
    "details": []
}
```
