# Presence Spec
Presences are Derailed's way of implementing statuses and activites.

## Presence Object

| field     | type      |
| --------- | --------- |
| user_id   | snowflake |
| status    | string    |
| content   | string    |
| timestamp | timestamp |

* content is maxed at 128 length.
