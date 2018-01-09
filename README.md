# node-bitcoin-rpc

[![Circle CI](https://circleci.com/gh/drazisil/node-bitcoin-rpc.svg?style=shield)](https://circleci.com/gh/drazisil/node-bitcoin-rpc) [![Coverage Status](https://coveralls.io/repos/drazisil/node-bitcoin-rpc/badge.svg?branch=master&service=github)](https://coveralls.io/github/drazisil/node-bitcoin-rpc?branch=master)
[![Greenkeeper badge](https://badges.greenkeeper.io/drazisil/node-bitcoin-rpc.svg)](https://greenkeeper.io/)

nodejs json-rpc for bitcoin

## Instructions:

1. `require()` it
2. call `.init()` with host, port, username, password as args
3. call `.call()` with the method, param and callback (the callback takes (err, result))

* optional: call `.setTimeout()` with the number of milliseconds to wait if 500 isn't enough

## Example:

```
var bitcoin_rpc = require('node-bitcoin-rpc')

bitcoin_rpc.init('host', port, 'rpc_username', rpc_pass)
bitcoin_rpc.call('getbalance', [], function (err, res) {
  if (err) {
    let errMsg = "Error when calling bitcoin RPC: " + err;
    console.log(errMsg);
    throw new Error(errMsg);
  } else if (res.error) {
    let errMsg = "Error received by bitcoin RPC: " + res.error.message + " (" + res.error.code + ")";
    console.log(errMsg);
    throw new Error(errMsg);
  } else {
    console.log('Yay! I need to do whatever now with ' + res.result)
  }
})
```

## Defaults:

* host; localhost
* port: 8332
* rpc_username: bitcoinrpc
* rpc_password: foo
* connection timeout: 500 ms
