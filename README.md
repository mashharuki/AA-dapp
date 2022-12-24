# AA-dapp

Account Abstraction を学習するリポジトリです。

## コマンド系

- 初期設定ファイルの生成

```bash
yarn run init
```

```json
"scripts": {
    "lint": "eslint . && tsc --noEmit",
    "lint:fix": "eslint . --fix",
    "prettier": "prettier --check --ignore-path ./.eslintignore '**'",
    "prettier:fix": "prettier --write --ignore-path ./.eslintignore '**'",
    "init": "ts-node scripts/init.ts",
    "simpleAccount:address": "ts-node scripts/simpleAccount/address.ts",
    "simpleAccount:transfer": "ts-node scripts/simpleAccount/transfer.ts",
    "simpleAccount:erc20Transfer": "ts-node scripts/simpleAccount/erc20Transfer.ts",
    "simpleAccount:batchTransfer": "ts-node scripts/simpleAccount/batchTransfer.ts",
    "simpleAccount:batchErc20Transfer": "ts-node scripts/simpleAccount/batchErc20Transfer.ts"
}
```

- simpleAccount アドレスの生成

```bash
yarn run simpleAccount:address
```

結果

```bash
SimpleAccount address: 0x100cD9e97EdAEe0950d97f75251313e45213C8Fb
✨  Done in 1.56s.
```

- MATIC の送金コマンド

```bash
yarn run simpleAccount:transfer 0x1431ea8af860C3862A919968C71f901aEdE1910E 0.03
```

結果

```bash
Signed UserOperation: {
  "sender": "0x100cD9e97EdAEe0950d97f75251313e45213C8Fb",
  "nonce": "0x0",
  "initCode": "0xe19e9755942bb0bd0cccce25b1742596b8a8250b3bf2c3e700000000000000000000000078d4f01f56b982a3b03c4e127a5d3afa8ebee68600000000000000000000000051908f598a5e0d8f1a3babfa6df76f9704dad0720000000000000000000000000000000000000000000000000000000000000000",
  "callData": "0x80c5c7d00000000000000000000000001431ea8af860c3862a919968c71f901aede1910e000000000000000000000000000000000000000000000000006a94d74f43000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000",
  "callGasLimit": "0x5580",
  "verificationGasLimit": "0x129727",
  "maxFeePerGas": "0xa2c22e83",
  "maxPriorityFeePerGas": "0xa2c22e65",
  "paymasterAndData": "0x",
  "preVerificationGas": "0xc644",
  "signature": "0xff954fe43538bf8fff0f928aa03f58c62b7c28d9b14912c4e1b452853124bd622053de4915a85e55697f714e80bf7668670e043467d2116df33979a1c2fd2f551b"
}
UserOpHash: 0x854c14b08bd913b7960edc3d4cbef6d65666e20e1494c4a0831a46cb18829fd1
Waiting for transaction...
Transaction hash: 0xc561b6a5410ffc8c10bd36b4102a08e57dc92040e4706526c3acedc42143d20d
✨  Done in 13.44s.
```

### 参考文献

1. [Stackup](https://www.stackup.sh/)
2. [EIP-4337: Account Abstraction using alt mempool](https://eips.ethereum.org/EIPS/eip-4337)
3. [Stackup Docs](https://docs.stackup.sh/)
4. [Stackup QuickStart](https://docs.stackup.sh/docs/guides/quickstart)
5. [Stackup QuickStart Video](https://www.youtube.com/watch?v=zvnm2GnMAts)
6. [【GitHub】erc-4337-examples](https://github.com/stackup-wallet/erc-4337-examples)
7. [【Mumbai】entrypoint Contract](https://mumbai.polygonscan.com/address/0x78d4f01f56b982a3B03C4E127A5D3aFa8EBee686#code)
8. [stackup-bundler](https://github.com/stackup-wallet/stackup-bundler)
9. [Stackup dashboard](https://app.stackup.sh/dashboard)
