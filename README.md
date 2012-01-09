## Overview

This is a Node.js library for integrating with the [Braintree](http://www.braintreepayments.com) gateway.

The library is a work in progress and a few features are still missing. Until
we hit version 1.0 we may break backwards compatibility, but the changes
should be minimal. We're using [semantic versioning](http://semver.org/).
[Email us](mailto:support@braintreepayments.com) if you have any questions.

## Installing

### From NPM

* `npm install braintree`
* `var braintree = require('braintree')`

### From Source

* clone the latest tag somewhere in your require.paths
* `var braintree = require('braintree-node/lib/braintree')`

### Dependencies

* node ~0.6.6
* coffee-script ~1.1
* xml2js >= 0.1.13

## Not Yet Implemented

* search APIs (transactions, vault, subscriptions, expired cards)

## Links

* [Documentation](http://www.braintreepayments.com/docs/node)
* [Bug Tracker](http://github.com/braintree/braintree_node/issues)

## Quick Start
```javascript
var sys = require('sys'),
    braintree = require('braintree');

var gateway = braintree.connect({
  environment: braintree.Environment.Sandbox,
  merchantId: 'your_merchant_id',
  publicKey: 'your_public_key',
  privateKey: 'your_private_key'
});

gateway.transaction.sale({
  amount: '5.00',
  creditCard: {
    number: '5105105105105100',
    expirationDate: '05/12'
  }
}, function (err, result) {
  if (err) throw err;

  if (result.success) {
    sys.puts('Transaction ID: ' + result.transaction.id);
  } else {
    sys.puts(result.message);
  }
});
```

## License

See the LICENSE file.