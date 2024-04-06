# Handling Errors

When running SplitScript, an unhandled error will crash your process

We proved a handleError function that will catch all errors from your listeners

```typescript
import { handleError } from '@splitscript.js/core'

handleError((data, error) => {
        console.log("There was an error: ", error)
})
// You can add multiple error handlers
handleError((data, error) => {
        console.log("There was an error: ", error)
})
```

{% hint style="warning" %}
Make sure you put the handleError function at the start of your code
{% endhint %}
