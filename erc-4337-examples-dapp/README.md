![](https://i.imgur.com/Ym2VV8z.png)

# Getting started

A collection of example scripts for working with ERC-4337. For an overview on the EIP and account abstraction, see our docs [here](https://docs.stackup.sh/).

All scripts in this repository is built using [@account-abstraction/sdk](https://www.npmjs.com/package/@account-abstraction/sdk). The implementation of all the following commands are located in the [scripts directory](./scripts/).

## Table of contents

- [Setup](#setup)
  - [Init config](#init-config)
    - [`bundlerUrl`](#bundlerurl)
    - [`rpcUrl`](#rpcurl)
    - [`signingKey`](#signingkey)
    - [`entryPoint`](#entrypoint)
    - [`simpleAccountFactory`](#simpleAccountFactory)
- [Commands](#commands)
  - [Simple Account](#simple-account)
    - [Get account address](#get-account-address)
    - [Transfer ETH](#transfer-eth)
    - [Transfer ERC-20 token](#transfer-erc-20-token)
    - [Batch transfer ETH](#batch-transfer-eth)
    - [Batch transfer ERC-20 token](#batch-transfer-erc-20-token)
- [License](#license)
- [Contact](#contact)

# Setup

Clone this repo into your local environment:

```bash
git clone git@github.com:stackup-wallet/erc-4337-examples.git
```

Install dependencies:

```bash
yarn install
```

## Init config

These config values will be used for all documented [commands](#commands).

```bash
yarn run init
```

### `bundlerUrl`

**Default value is set to `http://localhost:4337`.**

All UserOperations are required to be sent to a bundler. This field specifies the URL for the bundler you want to use.

You can run a self-hosted instance with [stackup-bundler](https://github.com/stackup-wallet/stackup-bundler). **Fully managed instances are also available. If you would like one setup, come [talk to us](https://discord.gg/FpXmvKrNed)!**

### `rpcUrl`

**Default value is set to `https://rpc-mumbai.maticvigil.com/`.**

This is a standard RPC URL for an ethereum node. By default it uses the public RPC for Polygon mumbai testnet. You can change this to any network you like.

### `signingKey`

**Default value is randomly generated with ethers.js.**

All UserOperations have a `signature` field which smart contract accounts will use to validate transactions. This key will be used to sign all UserOperations and set as the owner for the smart contract account.

### `entryPoint`

**Default value is set to `0x78d4f01f56b982a3B03C4E127A5D3aFa8EBee686`.**

This is address of the singleton EntryPoint contract. It is the same on all networks.

### `simpleAccountFactory`

**Default value is set to `0xe19E9755942BB0bD0cCCCe25B1742596b8A8250b`.**

This is factory address for deploying [SimpleAccount.sol](https://github.com/eth-infinitism/account-abstraction/blob/develop/contracts/samples/SimpleAccount.sol). It is the same on all networks and allows us to generate deterministic addresses.

# Commands

Once you have an environment setup, these commands can be used for running the example scripts.

The location of each script mimics the command structure. For example `yarn run simpleAccount:address` will be located in `scripts/simpleAccount/address.ts`

## Simple Account

Scripts for managing accounts based on [SimpleAccount.sol](https://github.com/eth-infinitism/account-abstraction/blob/develop/contracts/samples/SimpleAccount.sol).

### Get account address

Smart contract account addresses can be deterministically generated. Use this command to get your account address based on the `signingKey` set in your `config.json`.

The account will be automatically deployed on the first transaction.

```bash
yarn run simpleAccount:address
```

### Transfer ETH

Before executing a transfer, make sure to deposit some ETH to the address generated by the `simpleAccount:address` command.

```bash
yarn run simpleAccount:transfer <recipient-address> <eth-amount>
```

### Transfer ERC-20 token

Make sure the address generated by `simpleAccount:address` has enough specified tokens to execute the transfer.

This command does not use a paymaster so make sure to also have enough ETH to pay gas fees.

```bash
yarn run simpleAccount:erc20Transfer <token-address> <recipient-address> <token-amount>
```

### Batch transfer ETH

This example shows how we can do multiple atomic ETH transfers in a single transaction.

```bash
# recipient-addresses is comma separated.
# e.g. 0x123..abc,0x456...def
yarn run simpleAccount:batchTransfer <recipient-addresses> <eth-amount>
```

### Batch transfer ERC-20 token

Similar to `simpleAccount:batchTransfer`, we can also do multiple atomic contract interactions in a single transaction. This example shows us how with an ERC-20 token.

```bash
# recipient-addresses is comma separated.
# e.g. 0x123..abc,0x456...def
yarn run simpleAccount:batchErc20Transfer <token-address> <recipient-addresses> <token-amount>
```

# License

Distributed under the MIT License. See [LICENSE](./LICENSE) for more information.

# Contact

Feel free to direct any technical related questions to the `dev-hub` channel in the [Stackup Discord](https://discord.gg/FpXmvKrNed).