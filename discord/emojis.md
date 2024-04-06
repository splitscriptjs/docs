# emojis

## list

Returns list of emojis in guild

```typescript
await discord.emojis.list(guildId)
```

## get

Returns emoji object for given guild and emoji ids

```typescript
await discord.emojis.get(guildId, emojiId)
```

## create

Creates a new emoji for a guild

```typescript
await discord.emojis.create(guildId, {fields})
```

| field | type          | description                     |
| ----- | ------------- | ------------------------------- |
| name  | string        | name of the emoji               |
| image | base64 string | the 128x128 image               |
| roles | Snowflake\[]  | roles allowed to use this emoji |

## edit

Edits the given emoji

```typescript
await discord.emojis.edit(guildId, emojiId, {fields})
```

| field  | type          | description                     |
| ------ | ------------- | ------------------------------- |
| name?  | string        | name of the emoji               |
| roles? | ?Snowflake\[] | roles allowed to use this emoji |

## delete

Deletes the given emoji

```typescript
await discord.emojis.delete(guildId, emojiId)
```

## classes

## Emoji

### properties

| property         | type      | description                                                               |
| ---------------- | --------- | ------------------------------------------------------------------------- |
| id               | Snowflake | emoji id                                                                  |
| name             | ?string   | emoji name                                                                |
| roles?           | string\[] | roles allowed to use this emoji                                           |
| user?            | User      | user that created this emoji                                              |
| require\_colons? | boolean   | whether this emoji must be wrapped in colons                              |
| managed?         | boolean   | whether this emoji is managed                                             |
| animated?        | boolean   | whether this emoji is animated                                            |
| available?       | boolean   | whether this emoji can be used, may be false due to loss of Server Boosts |
| guild\_id        | Snowflake | id of guild this emoji is in                                              |

### methods

#### get

Gets this emoji (Updates this class instance)

```typescript
await emoji.get()
```

#### edit

Edits this emoji (Updates this class instance)

```typescript
await emoji.edit({fields})
```

[fields](emojis.md#edit)

#### delete

Deletes this emoji

```typescript
await emoji.delete()
```
