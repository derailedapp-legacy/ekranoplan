# POST /users/@me/group-dms: Created 201
Creates a new Group DM Track.

You must be friends with each user added.

Returns a [track object](../../objects/track.md#track-object).

### Headers

* Authorization - User Token

### Payload

| field     | type                      |
| --------- | ------------------------- |
| name      | string                    |
| topic     | string                    |
| user_ids  | list of users to invite   |

# PATCH /tracks/{track_id}: Success 200
Modifies a Track.

Requires the `MODIFY_TRACKS` permission in guilds.

Returns a [track object](../../objects/track.md#track-object).

### Headers

* Authorization - User Token

### Payload

**If a field is set to null, it is excluded EXCEPT for topic.**

**All fields here are optional.**

| field     | type                      |
| --------- | ------------------------- |
| name      | string                    |
| topic     | string                    |

# DELETE /tracks/{track_id}: No Content 204
Deletes a Track.

Requires the `DELETE_TRACKS` permission in guilds.

### Headers

* Authorization - User Token
