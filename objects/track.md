# Track Spec
Track's are Derailed's way of implementing Discord-like Channels for Guilds, and DM/Group DM Tracks.

Tracks are represented in many forms, and are dispersed over a large set of types, 
so it may be hard to try and track these internally.

## Track Object

| field             | type                                              |
| ----------------- | ------------------------------------------------- |
| id                | snowflake                                         |
| guild_id??        | snowflake                                         |
| icon              | string                                            |
| name              | string                                            |
| topic?            | string                                            |
| position          | integer                                           |
| type              | integer                                           |
| members??         | list of [users](./user.md#user-object)            |
| nsfw???           | boolean                                           |
| last_message_id?  | snowflake                                         |
| parent_id??       | snowflake                                         |
| overwrites??      | list of [overwrite objects](#overwrite-object)    |

## Overwrite Object

| field | type      |
| ----- | --------- |
| id    | snowflake |
| type  | integer   |
| allow | integer   |
| deny  | integer   |

* "integer" for allow and deny is a track permissions bitset.
* type - one of 1 user or 2 role.

## Message Object

| field             | type                  |
| ----------------- | --------------------- |
| id                | snowflake             |
| author_id         | snowflake             |
| track_id          | snowflake             |
| timestamp         | ISO8601 timestamp     |
| edited_timestamp  | ISO8601 timestamp     |
| mention_everyone  | boolean               |
| pinned            | boolean               |
| type              | integer               |
| content           | string                |

## Pin Object
This is only a DB Object.

Max pins for a channel is 3000.

| field         | type      |
| ------------- | --------- |
| message_id    | snowflake |
| channel_id    | snowflake |

## Track Types

| name              | value |
| ----------------- | ----- |
| CATEGORY          | 0     |
| TEXT_TRACK        | 1     |
| DM_TRACK          | 2     |
| GROUP_DM_TRACK    | 3     |

