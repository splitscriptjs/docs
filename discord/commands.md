# commands

## create

Creates a command. Specify guildId to make a command in a guild

```typescript
await discord.commands.create({fields}, guildId)
```

| field                         | type             | description                                                                                                                                                                             |
| ----------------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name                          | string           | Name of command, 1-32 characters                                                                                                                                                        |
| name\_localizations?          | LocaleObject     | Localization dictionary for the `name` field. Values follow the same restrictions as `name`                                                                                             |
| description?                  | string           | 1-100 character description                                                                                                                                                             |
| description\_localizations?   | LocaleObject     | Localization dictionary for the `description` field. Values follow the same restrictions as `description`                                                                               |
| options?                      | CommandOption\[] | Parameters for the command                                                                                                                                                              |
| default\_member\_permissions? | ?string          | Set of permissions represented as a bit set                                                                                                                                             |
| default\_permissions?         | boolean          | Replaced by `default_member_permissions` and will be deprecated in the future. Indicates whether the command is enabled by default when the app is added to a guild. Defaults to `true` |
| type?                         | CommandType      | Type of command, defaults `1` if not set                                                                                                                                                |
| nsfw?                         | boolean          | Indicates whether the command is age-restricted                                                                                                                                         |

## delete

Deletes a command. You must specify guildId if it is a guild command

```typescript
await discord.commands.delete(commandId, guildId?)
```

## edit

Edits a command

```typescript
await discord.commands.edit(commandId, fields, guildId?)
```

| fields                        | type             | description                                                                                                                                                                             |
| ----------------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name?                         | string           | Name of command, 1-32 characters                                                                                                                                                        |
| name\_localizations?          | ?LocaleObject    | Localization dictionary for the `name` field. Values follow the same restrictions as `name`                                                                                             |
| description                   | string           | 1-100 character description                                                                                                                                                             |
| description\_localizations?   | ?LocaleObject    | Localization dictionary for the `description` field. Values follow the same restrictions as `description`                                                                               |
| options?                      | CommandOption\[] | Parameters for the command                                                                                                                                                              |
| default\_member\_permissions? | ?string          | Set of permissions represented as a bit set                                                                                                                                             |
| default\_permission?          | boolean          | Replaced by `default_member_permissions` and will be deprecated in the future. Indicates whether the command is enabled by default when the app is added to a guild. Defaults to `true` |
| nsfw?                         | boolean          | Indicates whether the command is age-restricted                                                                                                                                         |

## list

Get a list of commands. Specify guildId for commands in a specific guild

```typescript
await discord.commands.list(guildId?, withLocalizations?: boolean)
```

## bulkOverwrite

Overwrite a list of commands.

```typescript
await discord.commands.bulkOverwrite(fields[], guildId?)
```

| field                         | type             | description                                                                                                                                                                             |
| ----------------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id?                           | Snowflake        | ID of the command, if known                                                                                                                                                             |
| name                          | string           | Name of command, 1-32 characters                                                                                                                                                        |
| name\_localizations?          | ?LocaleObject    | Localization dictionary for the `name` field. Values follow the same restrictions as \`name                                                                                             |
| description                   | string           | 1-100 character description                                                                                                                                                             |
| description\_localizations?   | ?LocaleObject    | Localization dictionary for the `description` field. Values follow the same restrictions as `description`                                                                               |
| options?                      | CommandOption\[] | Parameters for the command                                                                                                                                                              |
| default\_member\_permissions? | ?string          | Set of permissions represented as a bit set                                                                                                                                             |
| dm\_permission?               | ?boolean         | Indicates whether the command is available in DMs with the app, only for globally-scoped commands. By default, commands are visible.                                                    |
| default\_permission?          | ?boolean         | Replaced by `default_member_permissions` and will be deprecated in the future. Indicates whether the command is enabled by default when the app is added to a guild. Defaults to `true` |
| type?                         | CommandType      | Type of command, defaults `1` if not set                                                                                                                                                |
| nsfw?                         | boolean          | Indicates whether the command is age-restricted                                                                                                                                         |

## get

Get a command. You must specify guildId if it is a guild command

```typescript
await discord.commands.get(commandId, guildId?)
```

## classes

### Command

properties

| field                        | type             | description |
| ---------------------------- | ---------------- | ----------- |
| id                           | Snowflake        |             |
| type?                        | number           |             |
| application\_id?             | Snowflake        |             |
| guild\_id?                   | Snowflake        |             |
| name                         | string           |             |
| name\_localizations?         | ?LocaleObject    |             |
| description                  | string           |             |
| description\_localizations?  | ?LocaleObject    |             |
| options?                     | CommandOption\[] |             |
| default\_member\_permissions | ?string          |             |
| dm\_permission?              | ?boolean         |             |
| default\_permission?         | ?boolean         |             |
| nsfw?                        | boolean          |             |
| version                      | string           |             |

#### methods

#### edit

Edits this command

```typescript
await command.edit(fields)
```

[#edit](commands.md#edit "mention")fields

#### delete

deletes this command

```typescript
await command.delete()
```

#### get

Gets the latest version of this command

```typescript
await command.get()
```

#### getPermissions

Get the permissions of the command

```typescript
await command.getPermissions(guildId?)
```

