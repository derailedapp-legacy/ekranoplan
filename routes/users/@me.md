## POST /register: Created 201
Make a new user.

Returns a [user object](../../objects/user.md#user-object) with an extra `token` field.

### Payload

| field     | type   |
| --------- | ------ |
| email     | string |
| username  | string |
| password  | string |

### Example

```json
{
    "email": "example@example.com",
    "username": "example",
    "password": "example"
}
```

## POST /login: Success 200
Returns a token.

i.e.:

```json
{
    "token": "..."
}
```

### Payload

| field     | type   |
| --------- | ------ |
| username  | string |
| password  | string |

### Example

```json
{
    "email": "example@example.com",
    "password": "example"
}
```


## GET /users/@me: Success 200
Returns the current [user](../../objects/user.md#user-object).

### Headers

* Authorization - User Token

## GET /users/{user_id}: Success 200
Returns another [user](../../objects/user.md#user-object).

### Headers

* Authorization - User Token

## GET /users/@me/guilds: Success 200
Returns the current users' [guild objects](../../objects/guild.md#guild-object).

### Headers

* Authorization - User Token

## PATCH /users/@me: Success 200
Modifies, and returns the new [user object](../../objects/user.md#user-object).

Dispatches `USER_UPDATE`

Dispatches a `USER_DISCONNECT` if `password` is set.

### Headers

* Authorization - User Token

### Payload

**If a setting is set to null, it is excluded.**

**All fields here are optional.**

| field    | type   |
| -------- | ------ |
| username | string |
| email    | string |
| password | string |

### Example

```json
{
    "username": null,
    "email": "example@example.org",
    "password": "super secret password"
}
```

## POST /users/@me/delete: No Content 204
Deletes the users various objects.

Only errors if the password is invalid or missing or if the user is still in ownership of a guild.

Dispatches a `USER_DISCONNECT`

### Headers

* Authorization - User Token

### Payload

| field    | type   |
| -------- | ------ |
| password | string |

### Example

```json
{
    "password": "super secret password"
}
```