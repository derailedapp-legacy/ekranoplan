# User Spec
Derailed Users are its core interactor, 
they have unrestricted reign over many parts of the app and have the ability to do interact with things like relationships, dm channels, guilds, etc.

## User Object
The user object is meant to be simple, 
its done this way to save the amount of data needed to be sent and increase network speed.

| field         | type                  |
| ------------- | --------------------- |
| id            | snowflake             |
| username      | string                |
| discriminator | string                |
| email         | string                |
| password      | string                |
| verification  | verification object   |

* username - The users username, locked at 9000 uses, is their main identifier.
* discriminator - The users discriminator, their secondary piece of identification used so that names can't be squatted.
* password - The users password, hashed with argon2.

## Verification Object

* NOTE: This only has boolean types.

| field |
| ----- |
| email |
| phone |


## Profile Object

| field             | type                       |
| ----------------- | -------------------------- |
| id&               | snowflake                  |
| mutual_friends&&? | list of user snowflakes    |
| bio?              | string                     |

* mutual_friends - The mutual relations these users have
* bio - The user's about me or bio.

## Settings Object

| field         | type      |
| ------------- | --------- |
| id&           | snowflake |
| status        | string    |
| theme         | string    |
| client_status | string    |

* status - The user's status once "online," aka connected to the Gateway. This is what the default is when they connect. Can be online, dnd, afk, and invisible, defaults to online.
* theme - The user's current theme, dark or light. Defaults to dark.
* client_status - The user's current client, one of "mobile," "web," and "desktop".
