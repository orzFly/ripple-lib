#The Ripple JavaScript Library

[![Build Status](https://travis-ci.org/ripple/ripple-lib.svg?branch=develop)](https://travis-ci.org/ripple/ripple-lib) [![Coverage Status](https://coveralls.io/repos/ripple/ripple-lib/badge.png?branch=develop)](https://coveralls.io/r/ripple/ripple-lib?branch=develop)

[![NPM](https://nodei.co/npm/ripple-lib.png)](https://www.npmjs.org/package/ripple-lib)

`ripple-lib` connects to the Ripple network via the WebSocket protocol and runs in Node.js as well as in the browser.

###Use ripple-lib for:

+ Connecting to a local or remote rippled in JavaScript (Node.js or browser)
+ Issuing [rippled API](https://ripple.com/wiki/JSON_Messages) requests
+ Listening to events on the Ripple network (transaction, ledger, etc.)
+ Signing and submitting transactions to the Ripple network

###In this file:

1. Overview
2. [Getting `ripple-lib`](README.md#getting-ripple-lib)
3. [Quickstart](README.md#quickstart)
4. [Running tests](https://github.com/ripple/ripple-lib#running-tests)

###For additional documentation see:

1. [The `ripple-lib` Guides (docs/GUIDES.md)](docs/GUIDES.md)
2. [The `ripple-lib` API Reference (docs/REFERENCE.md)](docs/REFERENCE.md)
3. https://ripple.com/wiki/Ripple_JavaScript_library

###Also see:

+ https://ripple.com/wiki  
+ https://ripple.com

##Getting `ripple-lib`

**Via npm for Node.js**

```
  $ npm install ripple-lib
```

**Building ripple-lib for browser client**

```
  $ git clone https://github.com/ripple/ripple-lib
  $ npm install
  $ npm run build
```

Then use the minified `build/ripple-*-min.js` in your webpage

##Quickstart

`Remote` ([remote.js](https://github.com/ripple/ripple-lib/blob/develop/src/js/ripple/remote.js)) is the module responsible for managing connections to `rippled` servers:

```js
/* Loading ripple-lib with Node.js */
var Remote = require('ripple-lib').Remote;

/* Loading ripple-lib in a webpage */
// var Remote = ripple.Remote;

var remote = new Remote({
  // see the API Reference for available options
  trusted:        true,
  local_signing:  true,
  local_fee:      true,
  fee_cushion:     1.5,
  servers: [
    {
        host:    's1.ripple.com'
      , port:    443
      , secure:  true
    }
  ]
});

remote.connect(function() {
  /* remote connected */

  // see the API Reference for available functions
});
```

See [The `ripple-lib` Guides](docs/GUIDES.md) and [The `ripple-lib` API Reference](docs/REFERENCE.md) for walkthroughs and details about all of the available functions and options.

##Running tests

1. Clone the repository

2. `cd` into the repository and install dependencies with `npm install`

3. `npm test` or `make test` or `node_modules\.bin\mocha test\*-test.js` 

**Generating code coverage**

ripple-lib uses `istanbul` to generate code coverage. To create a code coverage report, run `npm test --coverage`. The report will be created in `coverage/lcov-report/`.
