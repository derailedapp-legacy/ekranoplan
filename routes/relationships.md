# GET /relationships/relatable?username=&discriminator=
### Headers

* Authorization - User Token

## Example

```json
{
    "user_id": "1234567890",
    "relatable": true
}
```

# GET /users/@me/relationships
Returns a list of [relationship objects](../objects/relationship.md#relationship-object).

### Headers

* Authorization - User Token

# PUT /relationships/{user_id}

### Headers

* Authorization - User Token

### Payload

| field | type    |
| ----- | ------- |
| type  | integer |

### Example

```json
{
    "type": 1
}
```

