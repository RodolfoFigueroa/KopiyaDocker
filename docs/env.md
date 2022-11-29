# Environment variables

## Postgres

Name                | Default               | Description                     | Required
---                 | ---                   | ---                             | :-:
`POSTGRES_HOST`     | `postgres`            | The Postgres host.              | ●
`POSTGRES_USER`     | `postgres`            | The Postgres user.              | ●
`POSTGRES_DB`       | `postgres`            | The Postgres database to use.   | ●
`POSTGRES_PASSWORD` | `averystrongpassword` | The Postgres database password. | ●

## Redis

Name                | Default               | Description                     | Required
---                 | ---                   | ---                             | :-:
`REDIS_HOST`        | `postgres`            | The Redis host.                 | ●
`REDIS_PORT`        | `postgres`            | The Redis port.                 | ●

## Discord

The variables in this section only need to be set if you select `discord` as a source.

Name                | Default               | Description                       | Required
---                 | ---                   | ---                               | :-:
`DISCORD_TOKEN`     |                       | Your bot's token.                 | 
`DISCORD_CLIENT_ID` |                       | Your application's client ID.     |
`DISCORD_DEV_GUILD` |                       | Your personal guild's (server) ID |

If `DISCORD_DEV_GUILD` is set, the bot will only broadcast commands to that specific guild. This is ideal if Kopiya is intended for your own personal use, as these updates happen instantly. 

On the other hand, if it's not set, the bot will publish commands to all available servers. The corresponding caches, however, take up to an hour to refresh, so it may take some time until your commands are available to use.

## Auth0

The variables in this section only need to be set if you intend to use the web frontend.

Name                | Default               | Description                        | Required
---                 | ---                   | ---                                | :-:
`AUTH_SECRET`       |                       | Your Auth0 application's secret    |
`AUTH_CLIENT_ID`    |                       | Your Auth0 application's client ID |
`ISSUER_BASE_URL`   |                       | Your Auth0 application's base URL  |