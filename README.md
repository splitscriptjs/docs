---
cover: .gitbook/assets/splitscript banner.png
coverY: 0
---

# 👋 Welcome to SplitScript.js

SplitScript.js - The <mark style="color:blue;">everything</mark> framework



Create your own packages with [Broken link](broken-reference "mention")\


## Install

```bash
$ npm i @splitscript.js/core
```

## Usage

We have a few packages

* [core](broken-reference) - for building your project through the CLI or for creating your own packages
* [discord](broken-reference) - for building discord bots!
* [https](broken-reference) - for sending http(s) requests

## Project Structure

We use filesystem for sending events

An example project could look like this:

<pre><code>functions/
    message/
        create/
            1.js
        delete/
            1.js
            
.env
app.js

<strong>ss.json
</strong>package.json
</code></pre>
