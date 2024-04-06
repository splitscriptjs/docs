# root

Set and get the project root

This overwrites the `actual.require.main.filename` - might not work when using something like PM2



## set

You can set the project root by calling `root` with the dir parameter

```typescript
import {root} from '@splitscript.js/core'

root('C:\\Path\\To\\Project')
```

## get

You can get the project root by calling `root` without any parameters

```typescript
import {root} from '@splitscript.js/core'

const projectRoot = root()
```
