# POST /guilds/{guild_id}/tracks: Created 201
Creates a new track for this Guild.

Requires the `CREATE_TRACKS` permission.

returns a [track object](../../objects/track.md#track-object).

### Headers

* Authorization - User Token

### Payload

| field         | type      |
| ------------- | --------- |
| name          | string    |
| parent_id??   | snowflake |
| position??    | integer   |
| topic??       | string    |
| type          | integer   |

### Example

```json
{
    "type": 1,
    "name": "2022",
    "topic": "It's 2022"
}
```

# PATCH /guilds/{guild_id}/tracks: No Content 204
Partially modifies the tracks in this guild.

Requires the `MODIFY_TRACKS` permission.

### Headers

* Authorization - User Token

### Payload
list of:

| field     | type      |
| --------- | --------- |
| id        | snowflake |
| position  | integer   |
| sync      | boolean   |
| parent_id | snowflake |
