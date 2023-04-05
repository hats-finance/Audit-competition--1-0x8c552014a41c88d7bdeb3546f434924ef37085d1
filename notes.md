Breaking changes:

- General
  - `gasLimit` is now `gas`
- `signMessage`
  - `message` no longer accepts byte array.
  - Removed `UserRejectedRequestError` in favor of viem's internal error
- `readContract`
  - Removed `overrides` in favor of `blockNumber` & `blockTag`
- `readContracts`
  - Changed structure of return type (`allowFailure: true` returns an array of `{ error, result, status }[]` instead of `Result[]`)
  - Removed console.warn logs (these can be extracted from the `status` & `error` field now)
  - Removed `overrides` in favor of `blockNumber` & `blockTag`
- `multicall`
  - Changed structure of return type (`allowFailure: true` returns an array of `{ error, result, status }[]` instead of `Result[]`)
  - Removed console.warn logs (these can be extracted from the `status` & `error` field now)
  - Removed `overrides` in favor of `blockNumber` & `blockTag`
- `waitForTransaction`
  - Replaced `onSpeedUp` with `onReplaced`
- `signTypedData`
  - `value` renamed to `message`
  - `primaryType` is required
- `fetchBlockNumber`
  - now bigint
- `watchPendingTransactions`
  - callback now returns array of transactions
- `prepareWriteContract`
  - Removed `abi`, `address`, `functionName` from return value, they are now in `request`.
  - `request` now returns shape of viem's `WriteContractParameters` instead of ethers' `TransactionRequest`.
  - Removed `overrides` in favor of `eth_sendTransaction` args (`gas`, `maxFeePerGas`, `value`, etc): https://viem.sh/docs/contract/writeContract.html#parameters
- `writeContract`
  - Removed `overrides` in favor of `eth_sendTransaction` args (`gas`, `maxFeePerGas`, `value`, etc): https://viem.sh/docs/actions/wallet/sendTransaction.html#parameters
  - `wait` has been removed from return type, use `waitForTransaction` instead.
- `prepareSendTransaction`
  - No longer returns `gasLimit` – wallets will calculate this instead.
- `watchContractEvent`
  - callback now returns array of event logs, rather than positional decoded args + log.
- `useWaitForTransaction`
  - `onSpeedUp` has been removed in favor of `onReplaced`
- `fetchEnsAvatar`
  - Replaced `address` with `name`.
- `useEnsAvatar`
  - Replaced `address` with `name`.
- `useWatchPendingTransactions`
  - listener now returns array of transactions
- `usePrepareContractWrite`
  - Removed `overrides` in favor of `eth_sendTransaction` args (`gas`, `maxFeePerGas`, `value`, etc): https://viem.sh/docs/contract/writeContract.html#parameters
- `useContractWrite`
  - Removed `overrides` in favor of `eth_sendTransaction` args (`gas`, `maxFeePerGas`, `value`, etc): https://viem.sh/docs/contract/writeContract.html#parameters
- `useContract`
  - Removed. Use `getContract` instead.

TODO:

- Remove `types/contracts.ts` in favor of viem contract types
- ethers workaround: Remove `normalizeFunctionName` util
- ethers workaround: Remove `ContractMethodDoesNotExistError` error
- ethers workaround: Remove `minimizeContractInterface` util