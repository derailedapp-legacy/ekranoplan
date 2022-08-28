# GET /guilds/{guild_id}: Success 200
Returns a [guild object](../../objects/guild.md#guild-object).

### Headers

* Authorization - User Token

# GET /guilds/{guild_id}/preview: Success 200
Returns a [guild object](../../objects/guild.md#guild-object) with "member_count" and "online_count."

# POST /guilds: Created 201
Make a brand new guild.

Returns a [guild object](../../objects/guild.md#guild-object).

### Headers

* Authorization - User Token

### Payload

| field         | type      |
| ------------- | --------- |
| name          | string    |
| description   | string    |
| nsfw??        | boolean   |

### Example

```json
{
    "name": "BeRailed",
    "description": "The place to BE RAILED on DERAILED",
    "nsfw": true
}
```


# PATCH /guilds/{guild_id}: Success 200
Modify this guild.

Requires the `MODIFY_GUILD` permission.

Returns a [guild object](../../objects/guild.md#guild-object)

### Headers

* Authorization - User Token

### Payload

| field         | type      |
| ------------- | --------- |
| name          | string    |
| description   | string    |
| nsfw??        | boolean   |

### Example

**If a field is set to null, it is excluded.**

**All fields here are optional.**

```json
{
    "name": "Berailed",
    "description": "The place to BERAILED on DERAILED",
}
```

# DELETE /guilds/{guild_id}: No Content 204
Deletes this guild.

* Guilds with over 1000 members cannot be deleted via the API.

Requires you to be owner.

### Headers

* Authorization - User Token
