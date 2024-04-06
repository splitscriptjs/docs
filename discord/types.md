---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# types

## Embed

| property     | type                                    | description                               |
| ------------ | --------------------------------------- | ----------------------------------------- |
| title?       | string                                  | title of embed                            |
| type?        | string                                  | type of embed                             |
| description? | string                                  | description of embed                      |
| url?         | string                                  | url of embed                              |
| timestamp?   | string                                  | ISO8601 timestamp string of embed content |
| color?       | number                                  | color code of embed                       |
| footer?      | [EmbedFooter](types.md#embedfooter)     | footer information                        |
| image?       | [EmbedMedia](types.md#embedmedia)       | image information                         |
| thumbnail?   | [EmbedMedia](types.md#embedmedia)       | thumbnail information                     |
| video?       | [EmbedMedia](types.md#embedmedia)       | video information                         |
| provider?    | [EmbedProvider](types.md#embedprovider) | provider information                      |
| author?      | [EmbedAuthor](types.md#embedauthor)     | author information                        |
| fields?      | EmbedField\[]                           | fields information                        |

## EmbedFooter

| property          | type   | description                                                |
| ----------------- | ------ | ---------------------------------------------------------- |
| text              | string | footer text                                                |
| icon\_url?        | string | url of footer icon (only supports http(s) and attachments) |
| proxy\_icon\_url? | string | a proxied url of footer icon                               |

## EmbedMedia

| property    | type   | description                                                                            |
| ----------- | ------ | -------------------------------------------------------------------------------------- |
| url         | string | source url of media _(for `image`/`thumbnail`: only supports http(s) and attachments)_ |
| proxy\_url? | string | a proxied url of the media                                                             |
| height?     | number | height of media                                                                        |
| width?      | number | width of media                                                                         |

## EmbedProvider

| property | type   | description      |
| -------- | ------ | ---------------- |
| name?    | string | name of provider |
| url?     | string | url of provider  |

## EmbedAuthor

| property          | type   | description                                                |
| ----------------- | ------ | ---------------------------------------------------------- |
| name              | string | name of author                                             |
| url?              | string | url of author (only supports http(s))                      |
| icon\_url?        | string | url of author icon (only supports http(s) and attachments) |
| proxy\_icon\_url? | string | a proxied url of author icon                               |

## EmbedField

| property | type    | description                                     |
| -------- | ------- | ----------------------------------------------- |
| name     | string  | name of the field                               |
| value    | string  | value of the field                              |
| inline?  | boolean | whether or not this field should display inline |
