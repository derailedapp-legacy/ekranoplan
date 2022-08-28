# Role Spec
Roles are Derailed's way of implementing both: unique permissions, 
or vanity **roles** for a specific user or group of users.

Such examples can be given:

- Level Roles
- Moderation Roles
- Vanity Roles

## Role Object

| field         | type      |
| ------------- | --------- |
| id            | snowflake |
| name          | string    |
| hoist         | boolean   |
| permissions   | integer   |
| position      | integer   |
