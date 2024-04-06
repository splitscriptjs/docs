# bans

## list

Returns a list of ban objects for the users banned from this guild

params

| field   | type    | description                                    |
| ------- | ------- | ---------------------------------------------- |
| limit?  | integer | number of users to return (up to maximum 1000) |
| before? | user id | consider only users before given user id       |
| after?  | user id | consider only users after given user id        |

```typescript
await discord.bans.list('GUILD_ID', params? /* see above */)
```

Returns [#ban](bans.md#ban "mention")\[]

## get

Returns a ban object for the given user or errors if the ban cannot be found

```typescript
await discord.bans.get('GUILD_ID', 'USER_ID')
```

Returns [#ban](bans.md#ban "mention")

## create

Create a guild ban, and optionally delete previous messages sent by the banned user

| field                     | type    | description                                                             |
| ------------------------- | ------- | ----------------------------------------------------------------------- |
| delete\_message\_days?    | integer | number of days to delete messages for (0-7) - **deprecated**            |
| delete\_message\_seconds? | integer | number of seconds to delete messages for, between 0 and 604800 (7 days) |

```typescript
await discord.bans.create('GUILD_ID', 'USER_ID', options? /* see above */)
```

Returns [#ban](bans.md#ban "mention")

## remove

Remove the ban for a user

```typescript
await discord.bans.remove('GUILD_ID', 'USER_ID')
```

Returns `void`

## classes

### Ban

#### Fields

<table><thead><tr><th>field</th><th width="205">type</th><th>description</th></tr></thead><tbody><tr><td>reason</td><td>string | null | never</td><td>Reason for the ban - never when ban is returned from ban.create</td></tr><tr><td>user</td><td><a href="https://discord.com/developers/docs/resources/user#users-resource">User</a> | { id: Snowflake}</td><td>The banned user - only has id if ban is returned from ban.create</td></tr><tr><td>guild_id</td><td>Snowflake</td><td>The id of the guild that the user is banned in</td></tr></tbody></table>

#### Methods

### Get

Gets this ban and updates this class

```typescript
await ban.get()
```

### Remove

Removes this ban

```typescript
await ban.remove()
```
