# Gateway
The Gateway is Derailed's way of implementing real-time on-the-fly message fan-out and dispatching.

# Errors

## Non-critical Error Format
These errors are sent when things like data validation fails.

```json
{
    "op": 2,
    "type": null,
    "data": {
        "type": "YOU_DID_WRONG",
        "reason": "why you did wrong"
    }
}
```

These errors are sent using the websocket connection, and doesn't close the websocket connection.

## Critical Errors
Critical Errors are errors that disconnect you from the websocket connection.

| code | description                                                                                        |
| ---- | -------------------------------------------------------------------------------------------------- |
| 4000 | Invalid Identify data                                                                              |
| 4001 | Invalid Token                                                                                      |
| 4002 | Maximum concurrent connections every 5 seconds reached                                             |
| 4003 | Maximum daily connections (1000) reached.                                                          |
| 4004 | Message Receive Rate Limit (60/60) passed.                                                         |
| 4005 | Unsupported data type given/data type is not json                                                  |
| 4006 | Unknown exception occured                                                                          |
| 4007 | Unauthorized Rate Limit (1) passed. (This allows the user only to send IDENTIFY before their ready |
| 4008 | Forced Disconnection (i.e. password reset)                                                         |

# Connecting

## On Connection
Immediately after you connect, you will be sent the [HELLO](#hello) event.

## Identifying
Identifying is the form of giving information to the gateway which it will process to recognize who you are and add analytics to.

```json
{
    "op": 1,
    "d": {
        "token": "ODMwMDA5OTQ2NDI4ODY2NTY=.Yv5FAw.dgH15-sVI_Nmurd81yCH8jRRNOc",
        "properties": {
            "os": "windows",
            "browser": "chrome",
            "device": "computer",
            "library_github_repository": "https://github.com/derailedapp/derailed.js",
            "client_version": "0.1.6"
        }
    }
}
```

Once you identify, you will be sent the [ready](#ready) event.

## Get Guild Members
The Gateway is the only portal Derailed gives you letting you access guild members.

To trigger getting members from a guild, just send something like the following:

```json
{
    "op": 4,
    "d": {
        "guild_id": "1234567890",
        "limit": 0,
    }
}
```

Once sent, it will send you a `GUILD_MEMBER` event for each member.

# Events

## Index

| name            | description                           |
| --------------- | ------------------------------------- |
| [HELLO](#hello) | Dispatched on connection              |
| [READY](#ready) | Dispatches once the gateway is ready  |
| [USER_UPDATE](#user-update) | Dispatched when a user in one of your guilds was updated |
| [SETTINGS_UPDATE](#settings-update) | Dispatched when your settings have updated |
| [GUILD_MEMBER](#guild-member) | A Guild Member                    |

## Hello

| name       | type   |
| ---------- | ------ |
| session_id | string |

i.e.:

```json
{
    "op": 3,
    "t": null,
    "d": {
        "session_id": "b58aadf4de6deccce3954507e14c75de"
    }
}
```

## Ready

| name      | type                                          |
| --------- | --------------------------------------------- |
| user      | [User](./objects/user.md#user-object)         |
| settings  | [Settings](./objects/user.md#settings-object) |

i.e.:

```json
{
    "op": 0,
    "t": "READY",
    "d": {
        "user": {
            "id": "83000994642886656",
            "username": "VincentRPS",
            "discriminator": "8900",
            "email": "vincent@derailed.gg",
            "verification": {
                "email": false,
                "phone": false
            }
        },
        "settings": {
            "status": "online",
            "theme": "dark",
            "client_status": null
        }
    }
}
```

## User Update
The data is a user object.

## Settings Update
The data is a settings object.

## Guild Member
A member object with `guild_id`.

i.e.:

```json
{
    "op": 0,
    "t": "GUILD_MEMBER",
    "d": {
        "user": { ... },
        "guild_id": "1234567890",
        "nick": "Vincent The Great",
        "permissions": 0,
        "joined_at": "timestamp"
    }
}
```
