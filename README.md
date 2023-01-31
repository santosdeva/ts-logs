# ts-logs - under development
Understand what happens in your application. Manage your logs and audit the steps of each request.

<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/checks/4lessandrodev/ts-logs/main" 
 alt="checks" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/stars/4lessandrodev/ts-logs" 
 alt="stars" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/commits/4lessandrodev/ts-logs/main" 
 alt="commits" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/last-commit/4lessandrodev/ts-logs/main" 
 alt="last commit" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/license/4lessandrodev/ts-logs" 
 alt="license" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/dependabot/4lessandrodev/ts-logs" 
 alt="dependabot" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/tag/4lessandrodev/ts-logs" 
 alt="tags" 
 style="max-width: 100%;">
</a>
<a href="https://www.npmjs.com/package/ts-logs" rel="nofollow" class="keychainify-checked">
 <img src="https://badgen.net/github/closed-issues/4lessandrodev/ts-logs" 
 alt="issues" 
 style="max-width: 100%;">
</a>
<a href="https://github.com/4lessandrodev/ts-logs?branch=main" rel="nofollow" class="keychainify-checked">
 <img src="https://img.shields.io/codecov/c/github/dwyl/hapi-auth-jwt2.svg?maxAge=2592000" 
 alt="issues" 
 style="max-width: 100%;">
</a>

---

## About the lib

This package provide a sdk to manage logs.

---
## Documentation

Application in beta version.

Example

```ts
import { randomUUID } from 'node:crypto';
import { Log, Step } from 'ts-logs';

// any id or unique string value
const uid = randomUUID();

// create a global log
const global = Log.init({ name: 'First Log', uid, origin: 'https://global.com' });

// create steps
const info = Step.info({ message: 'Fetching api...', name: 'Request Login', method: 'POST' });
const error = Step.error({ message: 'Timeout', name: 'Login', stack: 'Error stack' });

// add steps to global log
const err = global.addSteps([ info, error ]);

// print or save logs
err.print();
err.writeLocal();

```

---
### Use as middleware

Express middleware on **beta** option.

```ts

import express from 'express';
import { stackLog } from 'ts-logs';

const app = express();
app.use(express.json());

// ...

// on last middleware on the place to handle errors use `stackLog`

app.user(stackLog({ writeLocal: true }));

app.liste(3000);

```
