# GET /guilds/{guild_id}/roles: Success 200
Returns a list of [role objects](../../objects/role.md#role-object).

### Headers

* Authorization - User Token

# GET /guilds/{guild_id}/roles/{role_id}: Success 200
Returns a [role object](../../objects/role.md#role-object).

### Headers

* Authorization - User Token

# POST /guilds/{guild_id}/roles: Created 301
Creates a new role in this guild

Requires the `MANAGE_ROLES` permission.

Returns a [role object](../../objects/role.md#role-object).

### Headers

* Authorization - User Token

### Payload

| field         | type      |
| ------------- | --------- |
| name          | string    |
| hoist         | boolean   |
| permissions?  | integer   |
| position      | integer   |

* permissions cannot have higher permissions than your current assigned permissions.
* position has to be under your highest roles' position.

### Example

```json
{
    "name": "Genshin Impact Simps",
    "hoist": false,
    "position": 0
}
```

# PATCH /guilds/{guild_id}/roles/{role_id}: Success 200
Modifies this role.

Requires the `MANAGE_ROLES` permission.

Returns a [role object](../../objects/role.md#role-object).

### Headers

* Authorization - User Token

### Payload

| field         | type      |
| ------------- | --------- |
| name          | string    |
| hoist         | boolean   |
| permissions   | integer   |
| position      | integer   |

* permissions cannot have higher permissions than your current assigned permissions.
* position has to be under your highest roles' position.

### Example

```json
{
    "name": "Genshin Impact Simp's",
    "hoist": true,
    "position": 1
}
```
