# automod

## list

Get a list of all rules currently configured for the guild

```typescript
await discord.automod.list('GUILD_ID')
```

## get

Get a single rule

```typescript
await discord.automod.get('GUILD_ID', 'RULE_ID')
```

## create

Create a new rule

| field              | type                                          | description                                                             |
| ------------------ | --------------------------------------------- | ----------------------------------------------------------------------- |
| name               | string                                        | the rule name                                                           |
| event\_type        | [EventType](automod.md#eventtype)             | the event type                                                          |
| trigger\_type      | [TriggerType](automod.md#triggertype)         | the trigger type                                                        |
| trigger\_metadata? | [TriggerMetadata](automod.md#triggermetadata) | the trigger metadata                                                    |
| actions            | [AutomodAction](automod.md#action)\[]         | the actions which will execute when the rule is triggered               |
| enabled?           | boolean                                       | whether the rule is enabled (`false` by default)                        |
| exempt\_roles?     | role\_id\[]                                   | the role ids that should not be affected by the rule (Maximum of 20)    |
| exempt\_channels?  | channel\_id\[]                                | the channel ids that should not be affected by the rule (Maximum of 50) |

```typescript
await discord.automod.create('GUILD_ID', rule /* above */)
```

## modify

Modify an existing rule

{% code overflow="wrap" fullWidth="false" %}
```typescript
await discord.automod.modify('GUILD_ID', 'RULE_ID', rule /* same as create but without trigger_type */)
```
{% endcode %}

## delete

Delete a rule

```typescript
await discord.automod.delete('GUILD_ID', 'RULE_ID')
```

## classes

### Rule

Fields

<table><thead><tr><th width="213">field</th><th>type</th><th>description</th></tr></thead><tbody><tr><td>id</td><td>Snowflake</td><td></td></tr><tr><td>guild_id</td><td>Snowflake</td><td></td></tr><tr><td>name</td><td>string</td><td></td></tr><tr><td>creator_id</td><td>Snowflake</td><td></td></tr><tr><td>event_type</td><td>1</td><td></td></tr><tr><td>trigger_type</td><td>1 | 3 | 4 | 5</td><td></td></tr><tr><td>trigger_metadata</td><td>object</td><td></td></tr><tr><td>actions</td><td><a href="https://discord.com/developers/docs/resources/auto-moderation#auto-moderation-action-object">AutomodAction</a>[]</td><td></td></tr><tr><td>enabled</td><td>boolean</td><td></td></tr><tr><td>exempt_roles</td><td>Snowflake[]</td><td></td></tr><tr><td>exempt_channels</td><td>Snowflake</td><td></td></tr></tbody></table>

## types

### EventType

| event type    | value  | description                                         |
| ------------- | ------ | --------------------------------------------------- |
| MESSAGE\_SEND | 1      | when a member sends or edits a message in the guild |

### Action

| field     | type                                        | description                                                               |
| --------- | ------------------------------------------- | ------------------------------------------------------------------------- |
| type      | [ActionType](automod.md#actiontype)         | the type of action                                                        |
| metadata? | [ActionMetadata](automod.md#actionmetadata) | additional metadata needed during execution for this specific action type |

### ActionType

| action type          | value | description                                                                                                                                                |
| -------------------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BLOCK\_MESSAGE       | 1     | blocks a member's message and prevents it from being posted. A custom explanation can be specified and shown to members whenever their message is blocked. |
| SEND\_ALERT\_MESSAGE | 2     | logs user content to a specified channel                                                                                                                   |
| TIMEOUT              | 3     | timeout user for a specified duration                                                                                                                      |

### ActionMetadata

| field             | type         | description                                                                            |
| ----------------- | ------------ | -------------------------------------------------------------------------------------- |
| channel\_id       | Snowflake ID | channel to which user content should be logged                                         |
| duration\_seconds | integer      | timeout duration in seconds                                                            |
| custom\_message?  | string       | additional explanation that will be shown to members whenever their message is blocked |

### TriggerMetadata

| field                  | type               | description                                                                       |
| ---------------------- | ------------------ | --------------------------------------------------------------------------------- |
| keyword\_filter?       | string\[]          | substrings which will be searched for in content (Maximum of 1000)                |
| regex\_patterns?       | string\[]          | regular expression patterns which will be matched against content (Maximum of 10) |
| presets?               | ( 1 \| 2 \| 3 )\[] | the internally pre-defined wordsets which will be searched for in content         |
| allow\_list?           | string\[]          | substrings which should not trigger the rule (Maximum of 100 or 1000)             |
| mention\_total\_limit? | integer            | total number of unique role and user mentions allowed per message (Maximum of 50) |

### TriggerType

| trigger type    | value  | description                                                          |
| --------------- | ------ | -------------------------------------------------------------------- |
| KEYWORD         | 1      | check if content contains words from a user defined list of keywords |
| SPAM            | 3      | check if content represents generic spam                             |
| KEYWORD\_PRESET | 4      | check if content contains words from internal pre-defined wordsets   |
| MENTION\_SPAM   | 5      | check if content contains more unique mentions than allowed          |
