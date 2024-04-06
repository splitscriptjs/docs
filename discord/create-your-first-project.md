# create your first project

## Install Dependencies

{% tabs %}
{% tab title="npm" %}
```bash
npm init -y

npm i @splitscript.js/discord dotenv
npm i -g @splitscript.js/core@latest

npm i --save-dev @types/node
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm init

pnpm i @splitscript.js/discord dotenv
pnpm i -g @splitscript.js/core@latest

pnpm i --save-dev @types/node
```
{% endtab %}

{% tab title="bun" %}
```bash
bun init

bun i @splitscript.js/discord dotenv
bun i -g @splitscript.js/core@latest

bun i --save-dev @types/node
```
{% endtab %}
{% endtabs %}

## Connect to Discord

### Creating a bot

Go to [https://discord.com/developers/applications](https://discord.com/developers/applications)

<details>

<summary>Create a bot</summary>

<img src="../.gitbook/assets/newapp (1).png" alt="Click &#x22;New Application&#x22;" data-size="original">

![Enter a name and click "Create"](../.gitbook/assets/create.png)

![Click "Reset Token"](<../.gitbook/assets/resettoken (1).png>)

![Click Copy](../.gitbook/assets/copy.png)

</details>

<details>

<summary>Invite your bot</summary>

![Click "Installation"](../.gitbook/assets/invitelink.png)

![Select "Discord Provided Link"](../.gitbook/assets/discordprovidedlink.png)

![Add "bot" scope and "Administrator" permissions](../.gitbook/assets/botadmin.png)

Open the install link

</details>

### Create an env file

{% code title=".env" %}
```
DISCORD_BOT_TOKEN=XXXX
```
{% endcode %}

### Import environment variables

In your editor of choice, create a app.ts file

{% code title="app.ts" %}
```typescript
import 'dotenv/config'
```
{% endcode %}

### Start listening

{% code title="app.ts" %}
```typescript
import discord from "@splitscript.js/discord";

discord.listen(process.env.DISCORD_BOT_TOKEN as string, {
    intents: []
})
```
{% endcode %}

### Get your bot online

You can now start the bot, by running

This command also provides boilerplate for listeners and automatic restarts when you save a file

```bash
splitscript dev app.ts
```

### Run code on start

You can run a function after the bot starts, by using the `ready` event

{% code title="functions/discord/ready/hello.ts" fullWidth="false" %}
```typescript
import { Events } from '@splitscript.js/discord';
export default async function (event: Events.Ready) {
    console.log(`Logged in as ${event.user.username}#${event.user.discriminator}`)
}
```
{% endcode %}

After saving this, look at your terminal. It should show the above message
