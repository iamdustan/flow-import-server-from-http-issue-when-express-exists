# Flow Import Bug Repro

The issue at hand is when attempting to import a node built-in when express@4.x
is installed from [`flow-typed`](https://github.com/flowtype/flow-typed).

To repro:

* `git clone`
* `yarn` (or `npm install`)
* `flow`

The only app code present is:

```jsx
/* @flow */
import type { Server } from 'http';
```

If we delete our `flow-typed` directory then Flow understands this to be the
`Server` class from node's `http` module. As is we get the following error:

```
Named import from module `http`
This module has no named export called `Server`.
```

