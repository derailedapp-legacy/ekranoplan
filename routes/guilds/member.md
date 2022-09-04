# POST /guilds/{guild_id}/members/{member_id}/ban: No Content 204
Bans this user.

Requires the `BAN_MEMBERS` permission.

### Headers

* Authorization - User Token
* X-Action-Reason - An optional field to set the reason for the ban. This **is not** sent to the user.

# PATCH /guilds/{guild_id}/members/{member_id}: Success 200
Modifies this member.

Requires the `MODIFY_MEMBERS` permission.

Returns a [member object](../../objects/guild.md#member-object).

### Headers

* Authorization - User Token

### Payload

**If a field is set to null, it is excluded.**

**All fields here are optional.**

| field | type      |
| ----- | --------- |
| nick  | string    |

### Example

```json
{
    "nick": "I AM VINCENT"
}
```

# PATCH /guilds/{guild_id}/members/{member_id}/nick: Success 200
Modifies this member.

Requires the `MODIFY_MEMBER_NICKNAMES` permission.

Returns a [member object](../../objects/guild.md#member-object).

### Headers

* Authorization - User Token

### Payload

**If nick is set to null, it removes the members nick.**

| field | type      |
| ----- | --------- |
| nick  | string    |

### Example

```json
{
    "nick": "I AM VINCENT"
}
```

# DELETE /guilds/{guild_id}/members/{member_id}: No Content 204
Kick this user.

Requires the `KICK_MEMBERS` permission.

### Headers

* Authorization - User Token
