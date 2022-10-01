# POST /tracks/{track_id}/messages: Created 201
Creates a new message.

Requires the `CREATE_MESSAGE` permission.

Returns a [message object](../../objects/track.md#message-object).

### Headers

* Authorization - User Token

### Payload

| field     | type      |
| --------- | --------- |
| content   | string    |

# PATCH /tracks/{track_id}/messages/{message_id}: Success 200
Modifies a message you've created.

Returns a [message object](../../objects/track.md#message-object).

### Headers

* Authorization - User Token

### Payload

| field     | type      |
| --------- | --------- |
| content   | string    |

# DELETE /tracks/{track_id}/messages/{message_id}: No Content 204
Deletes a previously sent message.

Requires the `DELETE_MESSAGES` permission.

### Headers

* Authorization - User Token
