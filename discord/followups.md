# followups

## create

Creates a followup message

```typescript
await discord.followups.create(
    token: string, // Token of interaction
    {fields}
)
```

| field             | type                       | description                                                                   | required                         |
| ----------------- | -------------------------- | ----------------------------------------------------------------------------- | -------------------------------- |
| content           | string                     | the message contents (up to 2000 characters)                                  | One of content, files, or embeds |
| tts               | boolean                    | true if this is a TTS message                                                 | no                               |
| embeds            | [Embed](types.md#embed)\[] | embedded rich content                                                         | One of content, files, or embeds |
| allowed\_mentions | AllowedMentions            | allowed mentions for the message                                              | no                               |
| components        | Component\[]               | the components to include with the message                                    | no                               |
| files             | string\[]                  | the contents of the file being sent                                           | One of content, files, or embeds |
| attachments       | Partial\<Attachment>\[]    | attachment objects with filename and description                              | no                               |
| flags             | number                     | message flags combined as a bitfield (only `SUPPRESS_EMBEDS` can be set)      | no                               |
| thread\_name      | string                     | name of thread to create (requires the webhook channel to be a forum channel) | no                               |

## get

Gets a followup message

<pre class="language-typescript"><code class="lang-typescript"><strong>await discord.followups.get(token: string, messageId)
</strong></code></pre>

## edit

Edits a followup message

```typescript
await discord.followup.get(token: string, messageId, {fields})
```

## delete

Deletes a followup message

```typescript
await discord.followups.delete(token: string, messageId)
```

## classes

### FollowupMessage

#### properties

| property                  | type                       | description                                                                                                                                                                                                                                                             |
| ------------------------- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                        | Snowflake                  | id of the message                                                                                                                                                                                                                                                       |
| channel\_id               | Snowflake                  | id of the channel the message was sent in                                                                                                                                                                                                                               |
| author                    | User                       | the author of this message (not guaranteed to be a valid user)                                                                                                                                                                                                          |
| content                   | string                     | contents of the message                                                                                                                                                                                                                                                 |
| timestamp                 | string                     | when this message was sent                                                                                                                                                                                                                                              |
| edited\_timestamp         | ?string                    | when this message was edited (or null if never)                                                                                                                                                                                                                         |
| tts                       | boolean                    | whether this was a TTS message                                                                                                                                                                                                                                          |
| mention\_everyone         | boolean                    | whether this message mentions everyone                                                                                                                                                                                                                                  |
| mentions                  | User\[]                    | users specifically mentioned in the message                                                                                                                                                                                                                             |
| mention\_roles            | string\[]                  | roles specifically mentioned in this message                                                                                                                                                                                                                            |
| mention\_channels?        | ChannelMention\[]          | channels specifically mentioned in this message                                                                                                                                                                                                                         |
| attachments               | Attachment\[]              | any attached files                                                                                                                                                                                                                                                      |
| embeds                    | [Embed](types.md#embed)\[] | any embedded content                                                                                                                                                                                                                                                    |
| reactions                 | Reaction\[]                | reactions to the message                                                                                                                                                                                                                                                |
| nonce?                    | number \| string           | used for validating a message was sent                                                                                                                                                                                                                                  |
| pinned                    | boolean                    | whether this message is pinned                                                                                                                                                                                                                                          |
| webhook\_id?              | Snowflake                  | if the message is generated by a webhook, this is the webhook's id                                                                                                                                                                                                      |
| type                      | number                     | type of message                                                                                                                                                                                                                                                         |
| activity?                 | MessageActivity            | sent with Rich Presence-related chat embeds                                                                                                                                                                                                                             |
| application?              | Partial\<Application>      | sent with Rich Presence-related chat embeds                                                                                                                                                                                                                             |
| application\_id?          | Snowflake                  | if the message is an Interaction or application-owned webhook, this is the id of the application                                                                                                                                                                        |
| message\_reference?       | MessageReference           | data showing the source of a crosspost, channel follow add, pin, or reply message                                                                                                                                                                                       |
| flags?                    | number                     | message flags combined as a bitfield                                                                                                                                                                                                                                    |
| referenced\_message?      | ?Message                   | the message associated with the message\_reference                                                                                                                                                                                                                      |
| interaction?              | MessageInteraction         | sent if the message is a response to an Interaction                                                                                                                                                                                                                     |
| thread?                   | Channel                    | he thread that was started from this message, includes thread member object                                                                                                                                                                                             |
| components?               | Component\[]               | sent if the message contains components like buttons, action rows, or other interactive components                                                                                                                                                                      |
| sticker\_items?           | StickerItem\[]             | sent if the message contains stickers                                                                                                                                                                                                                                   |
| stickers?                 | Sticker\[]                 | the stickers sent with the message **(deprecated)**                                                                                                                                                                                                                     |
| position?                 | number                     | A generally increasing integer (there may be gaps or duplicates) that represents the approximate position of the message in a thread, it can be used to estimate the relative position of the message in a thread in company with total\_message\_sent on parent thread |
| role\_subscription\_data? | RoleSubscriptionData       | data of the role subscription purchase or renewal that prompted this ROLE\_SUBSCRIPTION\_PURCHASE message                                                                                                                                                               |
| token                     | string                     |                                                                                                                                                                                                                                                                         |

### methods

#### get

Gets this followup message (updates this class instance)

```typescript
await followup.get()
```

#### edit

Edits this followup message (updates this class instance)

```typescript
await followup.edit({fields})
```

[fields](followups.md#edit)

#### delete

Deletes this followup message

```typescript
await followup.delete()
```
