# Kopiya Docker

## Usage

This docker-compose starts a production-ready environment of the Kopiya backend, and (optionally) the web frontend.

## Deploying

### 1. Configuration

Copy the example `.env` file:

```
cp prod.env.dist prod.env
```

Open it with the editor of your choice and set the relevant environment variables. For more information on what each one does, read [the corresponding documentation](./docs/env.md).

---

Copy the example `config.toml` file:

```
cp config.toml.dist config.toml
```

Open it with the editor of your choice, and tweak the settings to your liking. For more information, read [this](./docs/config.md).

---

If you wish to use the web frontend, uncomment the lines under the `web` section inside the `docker-compose`. Keep in mind that this requires an Auth0 application, with the corresponding environment variables. 

### 2. Running

After configuring all relevant variables, type:

```
docker compose up
```

### 3. Adding and activating a Replika

If you enabled the web frontend, simply visit `localhost:3000` in your browser, and follow the prompts.

Otherwise, shell into your conntainer:

```
docker exec -it kopiya bash
```

Add a Replika:

```
node ./script/add_user.js
```

Note the reported user ID, since you'll need it to generate a temporary token:

```
node ./script/gen_token.js
```

Finally, in your Discord guild, type:

```
/register <your token>
```

### 4. (optional) Discord setup

If you selected Discord as a source for the first time, you must update the bot's commands, otherwise you won't be able to use them. 

First, start a shell session inside the main container:

```
docker exec -it kopiya bash
```

Register the commands:

```
node ./src/sources/discord/deploy_commands.js
```

If you set up a personal guild, you should see:

```
Started refreshing local application commands on guild <your guild ID>.
```

Otherwise:

```
Started refreshing global application commands.
```

Finally, if there are no errors, it should print:

```
Successfully reloaded application commands.
```

Now you can exit the shell and start using your Discord bot. However, if you did not set up a personal guild, it may take up to an hour for the changes to take effect. Do **not** run `deploy_commands` again, as this will only reset the timer.