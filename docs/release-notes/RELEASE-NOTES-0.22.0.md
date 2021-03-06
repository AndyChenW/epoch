# About this release

[This][this-release] is a maintenance release.
It:
* Adds on-chain forcing of progress for channel off-chain contracts. This impacts consensus. ([ref](https://github.com/aeternity/epoch/pull/1469), [ref](https://github.com/aeternity/epoch/pull/1528))
* Enriches HTTP API for fetching contract proof of inclusion with including contract's account as well. ([ref](https://github.com/aeternity/epoch/pull/1503))
* Improves stability of HTTP API ([ref](https://github.com/aeternity/epoch/pull/1505), [ref](https://github.com/aeternity/epoch/pull/1546))
* Fixes coinbase instruction in aevm. This impacts consensus. ([ref](https://github.com/aeternity/epoch/pull/1502))
* Makes it possible to use absolute TTLs in the Sophia oracle API. ([ref](https://github.com/aeternity/epoch/pull/1493))
* Improves channels' WebSocket client stability ([ref](https://github.com/aeternity/epoch/pull/1520))
* Enriches channel WebSocket client opening with the functionality of the `initator` giving the `responder` a certain amount of tokens in the initial channel state. This is an act of a good will and can as well be 0. ([ref](https://github.com/aeternity/epoch/pull/1531))
* Clarifies in the user HTTP API that the oracle extension TTL must be relative. ([ref](https://github.com/aeternity/epoch/pull/1537))
* Replaces '$' with '_' in addresses ([ref](https://github.com/aeternity/epoch/pull/1544))
* Improves checking and validation of gossiped light micro blocks([ref](https://github.com/aeternity/epoch/pull/1541))
* Changes `/key-blocks/pending` endpoint - the pending key block is returned even when the node is not mining ([ref](https://github.com/aeternity/epoch/pull/1536))
* Removes `pow` and `nonce` from pending key block and genesis block returned from HTTP API ([ref](https://github.com/aeternity/epoch/pull/1536))
* Adds `/key-blocks` endpoint for posting mined key blocks ([ref](https://github.com/aeternity/epoch/pull/1542))

[this-release]: https://github.com/aeternity/epoch/releases/tag/v0.22.0

This release introduces backward incompatible changes in the chain format:
* After upgrading your node, you will not have your previous balance (even if you keep your key pair);
* Please ensure that you do not reuse a persisted blockchain produced by the previous releases "v0.21.x".

Please join the testnet by following the instructions below, and let us know if you have any problems by [opening a ticket](https://github.com/aeternity/epoch/issues).
Troubleshooting of common issues is documented [in the wiki](https://github.com/aeternity/epoch/wiki/Troubleshooting).

The instructions below describe:
* [How to retrieve the released software for running a node](#retrieve-the-software-for-running-a-node);
* [How to install a node](#install-node);
* [How to join the testnet](#join-the-testnet).

## Retrieve the software for running a node

You can run a node by either:
* Installing the published [release binary][this-release] corresponding to your platform; or
* Running the published [Docker image `aeternity/epoch`][docker]; or
* [Building a release binary from source][build].

[docker]: https://github.com/aeternity/epoch/blob/v0.22.0/docs/docker.md
[build]: https://github.com/aeternity/epoch/blob/v0.22.0/docs/build.md

The user configuration is documented in the [wiki](https://github.com/aeternity/epoch/wiki/User-provided-configuration).
For specifying configuration using the Docker image, please refer to [its documentation][docker].

The node user API is documented:
* HTTP API endpoints are specified [online in swagger.yaml][swagger-yaml];
  * A JSON version of the same specification is located in the node at path `lib/aehttp-0.1.0/priv/swagger.json`.
  * The JSON version can be obtained from a running node using the endpoint `/api`.
  * An interactive visualization of the same specification is available [online][swagger-ui].
* WebSocket API endpoints are [specified online][api-doc];
* The intended usage of the user API (HTTP and WebSocket) is [documented online][api-doc].

[swagger-yaml]: https://github.com/aeternity/epoch/blob/v0.22.0/config/swagger.yaml
[swagger-ui]: https://aeternity.github.io/epoch-api-docs/?config=https://raw.githubusercontent.com/aeternity/epoch/v0.22.0/apps/aehttp/priv/swagger.json
[api-doc]: https://github.com/aeternity/protocol/blob/epoch-v0.22.0/epoch/api/README.md

## Install node

The instructions for installing a node using a release binary are in [the dedicated separate document](../../docs/installation.md).

For installation of a node using the Docker image, please refer to [its documentation online][docker].

## Join the testnet

This section describes how to run a node as part of the testnet - the public test network of nodes - by using the release binary.

For running a node as part of the testnet by using the Docker image, please consult [its documentation][docker] in addition to this section.

### Inspect the testnet

The core nodes of the public test network are accessible from the Internet.

Information, e.g. height, of the top block of the longest chain as seen by these core nodes of the testnet can be obtained by opening in the browser any of the following URLs:
* http://52.10.46.160:3013/v2/blocks/top
* http://18.195.109.60:3013/v2/blocks/top
* http://13.250.162.250:3013/v2/blocks/top
* http://31.13.249.70:3013/v2/blocks/top

### Setup your node

Setting up your node consists of:
* Configuring your node - see instructions in [the dedicated separate document](../../docs/configuration.md);
* Starting your node and verifying it works as expected - see instructions in [the dedicated separate document](../../docs/operation.md).
