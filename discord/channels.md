# channels

## get

Get a channel

```typescript
await discord.channels.get('CHANNEL_ID')
```

## list

Get a list of channels in a guild

```typescript
await discord.channels.list('GUILD_ID')
```

## create

| field                             | value                                           | description                                                                                                                                                                     |
| --------------------------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name                              | string                                          | channel name (1-100 characters)                                                                                                                                                 |
| type?                             | ?[ChannelType](channels.md#channeltype)         | the [type of channel](https://discord.com/developers/docs/resources/channel#channel-object-channel-types)                                                                       |
| topic?                            | ?string                                         | channel topic (0-1024 characters)                                                                                                                                               |
| bitrate?                          | ?number                                         | the bitrate (in bits) of the voice or stage channel; min 8000                                                                                                                   |
| user\_limit?                      | ?number                                         | the user limit of the voice channel                                                                                                                                             |
| rate\_limit\_per\_user?           | ?number                                         | amount of seconds a user has to wait before sending another message (0-21600); bots, as well as users with the permission `manage_messages` or `manage_channel`, are unaffected |
| position?                         | ?number                                         | sorting position of the channel                                                                                                                                                 |
| permission\_overwrites?           | Partial<[Overwrite](channels.md#overwrite)>\[]  | the channel's permission overwrites                                                                                                                                             |
| parent\_id?                       | ?channel id                                     | id of the parent category for a channel                                                                                                                                         |
| nsfw?                             | ?boolean                                        | whether the channel is nsfw                                                                                                                                                     |
| rtc\_region?                      | ?string                                         | channel [voice region](https://discord.com/developers/docs/resources/voice#voice-region-object) id of the voice or stage channel, automatic when set to null                    |
| video\_quality\_mode?             | ?number                                         | the camera [video quality mode](https://discord.com/developers/docs/resources/channel#channel-object-video-quality-modes) of the voice channel                                  |
| default\_auto\_archive\_duration? | ?number                                         | the default duration that the clients use (not the API) for newly created threads in the channel, in minutes, to automatically archive the thread after recent activity         |
| default\_reaction\_emoji?         | ?[DefaultReaction](channels.md#defaultreaction) | emoji to show in the add reaction button on a thread in a `GUILD_FORUM` channel                                                                                                 |
| available\_tags?                  | ?[ForumTag](channels.md#forumtag)               | set of tags that can be used in a `GUILD_FORUM` channel                                                                                                                         |
| default\_sort\_order?             | ?[SortOrderType](channels.md#sortordertype)     | the [default sort order type](https://discord.com/developers/docs/resources/channel#channel-object-sort-order-types) used to order posts in `GUILD_FORUM` channels              |

```typescript
await discord.channels.create('GUILD_ID', channel /* see above */)
```

## modify

Group DM

| field | value  | description                  |
| ----- | ------ | ---------------------------- |
| name? | string | 1-100 character channel name |
| icon? | string | base64 encoded icon          |

Guild channel

| field                                    | value                                             | description                                                                                                                                                                                                                   |
| ---------------------------------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name?                                    | string                                            | 1-100 character channel name                                                                                                                                                                                                  |
| type?                                    | [ChannelType](channels.md#channeltype)            | the type of channel; only conversion between text and announcement is supported and only in guilds with the "NEWS" feature                                                                                                    |
| position?                                | ?integer                                          | the position of the channel in the left-hand listing                                                                                                                                                                          |
| topic?                                   | ?string                                           | 0-1024 character channel topic (0-4096 characters for `GUILD_FORUM` channels)                                                                                                                                                 |
| nsfw?                                    | ?boolean                                          | whether the channel is nsfw                                                                                                                                                                                                   |
| rate\_limit\_per\_user?                  | ?integer                                          | amount of seconds a user has to wait before sending another message (0-21600); bots, as well as users with the permission `manage_messages` or `manage_channel`, are unaffected                                               |
| bitrate?                                 | ?integer                                          | the bitrate (in bits) of the voice or stage channel; min 8000                                                                                                                                                                 |
| user\_limit?                             | ?integer                                          | the user limit of the voice or stage channel, max 99 for voice channels and 10,000 for stage channels (0 refers to no limit)                                                                                                  |
| permission\_overwrites?                  | ?Partial<[Overwrite](channels.md#overwrite)>\[]   | channel or category-specific permissions                                                                                                                                                                                      |
| parent\_id?                              | ?Channel ID                                       | id of the new parent category for a channel                                                                                                                                                                                   |
| rtc\_region?                             | ?string                                           | channel [voice region](https://discord.com/developers/docs/resources/voice#voice-region-object) id, automatic when set to null                                                                                                |
| video\_quality\_mode?                    | ?[VideoQualityMode](channels.md#videoqualitymode) | the camera [video quality mode](https://discord.com/developers/docs/resources/channel#channel-object-video-quality-modes) of the voice channel                                                                                |
| default\_auto\_archive\_duration?        | ?integer                                          | the default duration that the clients use (not the API) for newly created threads in the channel, in minutes, to automatically archive the thread after recent activity                                                       |
| flags?                                   | integer                                           | [channel flags](https://discord.com/developers/docs/resources/channel#channel-object-channel-flags) combined as a [bitfield](https://en.wikipedia.org/wiki/Bit\_field). Currently only `REQUIRE_TAG` (`1 << 4`) is supported. |
| available\_tags?                         | [ForumTag](channels.md#forumtag)\[]               | the set of tags that can be used in a `GUILD_FORUM` channel; limited to 20                                                                                                                                                    |
| default\_reaction\_emoji?                | ?[DefaultReaction](channels.md#defaultreaction)   | the emoji to show in the add reaction button on a thread in a `GUILD_FORUM` channel                                                                                                                                           |
| default\_thread\_rate\_limit\_per\_user? | integer                                           | the initial `rate_limit_per_user` to set on newly created threads in a channel. this field is copied to the thread at creation time and does not live update.                                                                 |
| default\_sort\_order?                    | ?[SortOrderType](channels.md#sortordertype)       | the [default sort order type](https://discord.com/developers/docs/resources/channel#channel-object-sort-order-types) used to order posts in `GUILD_FORUM` channels                                                            |
| default\_forum\_layout                   | [ForumLayoutType](channels.md#forumlayouttype)    | the [default forum layout type](https://discord.com/developers/docs/resources/channel#channel-object-forum-layout-types) used to display posts in `GUILD_FORUM` channels                                                      |

thread

| field                    | value        | description                                                                                                                                                                                       |
| ------------------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name?                    | string       | 1-100 character channel name                                                                                                                                                                      |
| archived?                | boolean      | whether the thread is archived                                                                                                                                                                    |
| auto\_archive\_duration? | integer      | the thread will stop showing in the channel list after `auto_archive_duration` minutes of inactivity, can be set to: 60, 1440, 4320, 10080                                                        |
| locked?                  | boolean      | whether the thread is locked; when a thread is locked, only users with MANAGE\_THREADS can unarchive it                                                                                           |
| invitable?               | boolean      | whether non-moderators can add other non-moderators to a thread; only available on private threads                                                                                                |
| rate\_limit\_per\_user?  | ?integer     | amount of seconds a user has to wait before sending another message (0-21600); bots, as well as users with the permission `manage_messages`, `manage_thread`, or `manage_channel`, are unaffected |
| flags?                   | integer      | channel flags combined as a bitfield; `PINNED` can only be set for threads in forum channels                                                                                                      |
| applied\_tags?           | Snowflake\[] | the IDs of the set of tags that have been applied to a thread in a `GUILD_FORUM` channel; limited to 5                                                                                            |

Modify a channel

```typescript
await discord.channels.modify('CHANNEL_ID', channel /* see above */)
```

## delete

Delete a channel

```typescript
await discord.channels.delete('CHANNEL_ID')
```

## modifyPositions

| field              | value      | description                                                                      |
| ------------------ | ---------- | -------------------------------------------------------------------------------- |
| id                 | Snowflake  | channel id                                                                       |
| position?          | ?integer   | sorting position of the channel                                                  |
| lock\_permissions? | ?boolean   | syncs the permission overwrites with the new parent, if moving to a new category |
| parent\_id?        | ?Snowflake | the new parent ID for the channel that is moved                                  |

```typescript
await discord.channnels.modifyPositions('GUILD_ID', channels[] /* see above */)
```

## types

### VideoQualityMode

| mode | value | description                                         |
| ---- | ----- | --------------------------------------------------- |
| AUTO | 1     | Discord chooses the quality for optimal performance |
| FULL | 2     | 720p                                                |

### DefaultReaction

An object that specifies the emoji to use as the default way to react to a forum post. Exactly one of `emoji_id` and `emoji_name` must be set.

| field       | type       | description                        |
| ----------- | ---------- | ---------------------------------- |
| emoji\_id   | ?Snowflake | the id of a guild's custom emoji   |
| emoji\_name | ?string    | the unicode character of the emoji |

### ForumTag

| field       | type         | description                                                                                                    |
| ----------- | ------------ | -------------------------------------------------------------------------------------------------------------- |
| id          | Snowflake ID | the id of the tag                                                                                              |
| name        | string       | the name of the tag (0-20 characters)                                                                          |
| moderated   | boolean      | whether this tag can only be added to or removed from threads by a member with the `MANAGE_THREADS` permission |
| emoji\_id   | ?Snowflake   | the id of a guild's custom emoji                                                                               |
| emoji\_name | ?string      | the unicode character of the emoji                                                                             |

### ForumLayoutType

| flag          | value | description                               |
| ------------- | ----- | ----------------------------------------- |
| NOT\_SET      | 0     | No default has been set for forum channel |
| LIST\_VIEW    | 1     | Display posts as a list                   |
| GALLERY\_VIEW | 2     | Display posts as a collection of tiles    |

### SortOrderType

| type             | value | description                                                    |
| ---------------- | ----- | -------------------------------------------------------------- |
| LATEST\_ACTIVITY | 0     | Sort forum posts by activity                                   |
| CREATION\_DATE   | 1     | Sort forum posts by creation time (from most recent to oldest) |

### ChannelType

| type                 | value | description                                                                                                                                                |
| -------------------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GUILD\_TEXT          | 0     | a text channel within a server                                                                                                                             |
| DM                   | 1     | a direct message between users                                                                                                                             |
| GUILD\_VOICE         | 2     | a voice channel within a server                                                                                                                            |
| GROUP\_DM            | 3     | a direct message between multiple users                                                                                                                    |
| GUILD\_CATEGORY      | 4     | an [organizational category](https://support.discord.com/hc/en-us/articles/115001580171-Channel-Categories-101) that contains up to 50 channels            |
| GUILD\_ANNOUNCEMENT  | 5     | a channel that [users can follow and crosspost into their own server](https://support.discord.com/hc/en-us/articles/360032008192) (formerly news channels) |
| ANNOUNCEMENT\_THREAD | 10    | a temporary sub-channel within a `GUILD_ANNOUNCEMENT` channel                                                                                              |
| PUBLIC\_THREAD       | 11    | a temporary sub-channel within a `GUILD_TEXT` or `GUILD_FORUM` channel                                                                                     |
| PRIVATE\_THREAD      | 12    | a temporary sub-channel within a `GUILD_TEXT` channel that is only viewable by those invited and those with the `MANAGE_THREADS`permission                 |
| GUILD\_STAGE\_VOICE  | 13    | a voice channel for [hosting events with an audience](https://support.discord.com/hc/en-us/articles/1500005513722)                                         |
| GUILD\_DIRECTORY     | 14    | the channel in a [hub](https://support.discord.com/hc/en-us/articles/4406046651927-Discord-Student-Hubs-FAQ) containing the listed servers                 |
| GUILD\_FORUM         | 15    | Channel that can only contain threads                                                                                                                      |

### Overwrite

| field | type      | description                   |
| ----- | --------- | ----------------------------- |
| id    | Snowflake | role or user id               |
| type  | integer   | either 0 (role) or 1 (member) |
| allow | string    | permission bit set            |
| deny  | string    | permission bit set            |
