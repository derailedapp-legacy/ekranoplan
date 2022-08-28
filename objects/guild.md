# Guild Spec
Guild's are Derailed's way of implementing Discord-like "Servers" which can be a community, or moreover a group of communities.

Derailed Guild's have an open-set of fleshed out features. 
Some, like Track, or Message are fleshed out outside of this document but most other's should be here for organizational purposes.

## Guild Object

| field             | type              |
| ----------------- | ----------------- |
| id                | snowflake         |
| name              | string            |
| owner_id          | snowflake         |
| icon              | string            |
| features          | list of string    |
| flags             | integer           |
| description       | string            |
| nsfw              | boolean           |
| member_count&&    | integer           |
| online_count&&    | integer           |

* name - Maxed at 100
* features - These are non-default features given to the guild.
* flags - A bitset of flags this guild has.
* description - A description of the guild given to users. Locked at the max of 1300 length.
* nsfw - If the guild is fully NSFW. If set to true, all tracks are automatically converted to NSFW tracks.
* member_count - The amount of members this guild has.
* online_count - The amount of **online** members this guild has.


* NOTE: With our current setup, 
in the future online_count could strain the db and since unlike discord we use
python for our notification system, we can't just count the amount of members with an online presence in the guild's node.

* NOTE: Maybe explore elixir for the notification system then?

## Member Object

| field          | type                                  |
| -------------- | ------------------------------------- |
| user_id&       | snowflake                             |
| guild_id&      | snowflake                             |
| user&&?        | [user object](./user.md#user-object)  |
| nick           | string                                |
| permissions&&? | integer                               |
| joined_at?     | ISO8601 timestamp                     |


## Permissions

* NOTE: In a theoretical sense, the owner would inherit all of these permissions.

| name                      | bit    |
| ------------------------- | ------ |
| MODIFY_GUILD              | 1 << 0 |
| KICK_USERS                | 1 << 1 |
| MODIFY_MEMBERS            | 1 << 2 |
| MODIFY_MEMBER_NICKNAMES   | 1 << 3 |
| BAN_MEMBERS               | 1 << 4 |
| CREATE_TRACKS             | 1 << 5 |
| MODIFY_TRACKS             | 1 << 6 |
| DELETE_TRACKS             | 1 << 7 |
