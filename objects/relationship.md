# Relationship Spec
Relationship's are Derailed's way of implementing friends, friend requests, or blocks.

Relationships can be duplicated because of their duality nature.

Blocks aren't duplicated, but friends or friend requests can be.

The max relationships someone can have is 6000.

## Relationship Object

| field     | type      |
| --------- | --------- |
| user_id   | snowflake |
| target_id | snowflake |
| type      | integer   |

* user_id and target_id are shown only in the database. user_id will be removed and target_id will be transformed to user (being an object)

## Relationship Types

| name              | value |
| ----------------- | ----- |
| FRIEND            | 0     |
| FRIEND_REQUEST    | 1     |
| BLOCKED           | 2     |
