# getting started

## install

to install run this command

```bash
npm i '@splitscript.js/discord'
```

## listen for events

to listen for events, use the discord.listen function

```typescript
import discord from '@splitscript.js/discord'

discord.listen('TOKEN', {
    // It's recommended to set some intents so you can recieve more events
    intents: ['guild_messages', 'message_content']
})
```

## or login

you can also just login if you only want to use APIs

```typescript
import discord from '@splitscript.js/discord'

discord.login('TOKEN')
```
