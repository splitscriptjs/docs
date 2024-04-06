# usage

## install

```bash
npm i @splitscript.js/https
```

## import

```javascript
// commonjs
const https = require('@splitscript.js/https');

// esm
import https from '@splitscript.js/core'
```

## send a request

```typescript
await https.request(url: string, options: Request)
```

example

```typescript
// Send a GET request to https://httpbin.org/anything?hello="world"
const request = await https.request('https://httpbin.org/anything');
console.log(request.res)
// A https.IncomingMessage
console.log(request.data)
/*
{
  args: { hello: '"world"' },
  data: '',
  files: {},
  form: {},
  headers: {
    Host: 'httpbin.org'
  },
  json: null,
  method: 'GET',
  origin: '***.**.***.**',
  url: 'https://httpbin.org/anything'
}
*/
```

### send a body

<pre class="language-typescript"><code class="lang-typescript"><strong>await https.request('https://example.com', {body: 'this is a body!'})
</strong></code></pre>

### send URL params

<pre class="language-typescript"><code class="lang-typescript"><strong>// send a request to 'https://example.com?hello=world
</strong><strong>await https.request('https://example.com', { params: { hello: 'world' } })
</strong></code></pre>

### send a request with a method

You can specify `method` in your config like this:

```typescript
await https.request('https://example.com', { method: 'POST' })
```

or you can use `https.<method>` like this:

```typescript
await https.get('https://example.com')
await https.post('https://example.com')
await https.put('https://example.com')
await https.patch('https://example.com')
await https.delete('https://example.com')
```
