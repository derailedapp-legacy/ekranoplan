## GET /users/@me/settings: Success 200
Returns the users settings.

### Headers

* Authorization - User Token

## PATCH /users/@me/settings: Success 200
Edits, and returns the new [settings](../../objects/user.md#settings-object).

Dispatches a `SETTINGS_UPDATE`

### Payload

| field  | type   |
| ------ | ------ |
| status | string |
| theme  | string |

### Example

```json
{
    "status": "dnd",
    "theme": "light"
}
```