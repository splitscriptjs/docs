---
description: Send events to listener files in functions/
cover: ../.gitbook/assets/core EventEmitter.png
coverY: 0
---

# EventEmitter

## Register an Event Emitter

```typescript
import {EventEmitter} from '@splitscript.js/core'
const emitter = new Emitter(
    // folder under `projectroot/functions/` for events to be sent)
    folderName: string,
    // name of this package (should export Events for intellisense)
    packageName: string,
    // possible events (used in the CLI for creating listeners) 
    validEvents: string[]
);
```

#### Example

{% code overflow="wrap" %}
```typescript
import {EventEmitter} from '@splitscript.js/core'
const emitter = new Emitter(
    'discord', // listeners will be created in projectroot/functions/discord/
    '@splitscript.js/discord', // types will be imported from '@splitscript.js/discord'.Events
    ['message/create', 'message\delete', 'interaction_create', 'channel.create'] // These will be split by /, \, _, or . So creating a message.create listener will create a file in projectroot/functions/discord/message/create/
);
```
{% endcode %}

{% code title="mymodule/index.ts" %}
```typescript
export * as Events from './events'
```
{% endcode %}

{% code title="mymodule/events.ts" %}
```typescript
// type names should be in PascalCase
// e.g event message/create
export type MessageCreate = {
     id: string;
     channel_id: string;
     content: string;
}
```
{% endcode %}

## Send an event

```typescript
emitter.send(
    event: string[],
    data: object
);
```

#### Example

```typescript
// Call all function files in the functions/discord/message/create/ folder with the data {content: '1234'}
emitter.send(['message', 'create'], {content: '1234'});
```

## Get listener files

```typescript
// Get all listeners
emitter.listeners()
// Get listeners for specific event
emitter.listeners(['event', 'a'])
```

Returns `Promise<Listener[]>`

#### type Listener

```typescript
{
    // Folder names of the event (e.g ['message', 'create'])
    event: string[];
    // Path the listener is in (e.g D:\\myproject\\discord\\functions\\message\\create)
    path: string;
}
```
