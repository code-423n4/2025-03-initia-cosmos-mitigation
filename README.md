# Initia Cosmos Mitigation Review
- Total Prize Pool: $16,000 in USDC
  - Warden awards: $13,350 in USDC
  - Judge awards: $2,400 in USDC
  - Scout awards: $250 in USDC
- [Warden guidelines for C4 mitigation reviews](https://code4rena.notion.site/Guidelines-for-C4-mitigation-reviews-ed10fc5cfbf640bd8dcec66f38b343c4)
- Starts March 14, 2025 20:00 UTC
- Ends March 19, 2025 20:00 UTC 

## Important note 

Each warden must submit a mitigation review for *every* finding listed in the `Scope` section below. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all High and Medium issues will be considered in-scope and listed here.

- [F-10: minievm fails to charge intrinsic gas costs for EVM transactions, allowing the abuse of the accesslist to consume computational resources without proper compensation](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-10)
- [F-11: Explicit gas limit on low-level Solidity calls can be bypassed by dispatched EVM calls via the custom Cosmos precompile](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-11)
- [F-7: `ExecuteRequest`'s are not properly removed from the context queue](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-7)
- [F-9: JSON-RPC `FilterCriteria.Addresses` are unbound and can be used to DoS the RPC](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-9)
- [F-13: 	EVM stack overflow error leads to no gas being charged, which can be exploited to DoS the chain by dispatching EVM calls via the cosmos precompile](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-13)
- [F-135: Precompiles fail to charge gas in case of an error leading to a DOS vector](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-135)
- [F-3: Wrong handling of ERC20 denoms in `ERC20Keeper::BurnCoins`](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-3)
- [F-6: A regular Cosmos SDK message can be disguised as an EVM transaction, causing `ListenFinalizeBlock` to error which prevents the block from being indexed](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-6)
- [F-17: 	`GASLIMIT` opcode returns transaction gas limit instead of block gas limit resulting in incompatibility with the EVM](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-17)
- [F-19: Amino legacy signing method broken because of name mismatch](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-19)
- [F-26: MsgCreate2 deviates from EVM spec causing a large range of address not reachable](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-26)
- [F-1: setBeforeSendHook can never delete an existing store due to vulnerable validate](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-1)
- [F-112: IBC channel version negotiation bypass in IBC hooks middleware](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-112)
- [F-61: Pool fraction is not truncated when allocating the tokens allowing to receive more rewards than owed](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-61)
- [F-15: jsonutils precompile missing in access list](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-15)

## Scope

### Mitigation of High & Medium Severity Issues

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| [Link](https://github.com/initia-labs/minievm/pull/170/files) | F-10 | Intrinsic gas | 
| [Link](https://github.com/initia-labs/minievm/pull/165/commits/c7afb0edc4f1535d15423a3707d953ac48328971#diff-4aaff0c187848f578730cdb177b834f037f8f35b444dbdd87bb000129c45369b) | F-11 | Introduce to use submsg gas limit | 
| [Link](https://github.com/initia-labs/minievm/commit/1dd732449ea414b0e3c3f6efd085d38e11d058ed) | F-7 | Fix to maintain execute request on snapshot | 
| [Link](https://github.com/initia-labs/minievm/pull/165/commits/024640e8d972e73f9411adbddc8ea2c61a276e69) | F-9 | Add max addresses limit | 
| [Link](https://github.com/initia-labs/minievm/commit/7c83e01a2c6d5cfb28354f251de9897f700096e1) | F-13 | Change to return exact error only at simulate or checktx | 
| [Link](https://github.com/initia-labs/minievm/commit/7c83e01a2c6d5cfb28354f251de9897f700096e1) | F-135 | Change to return exact error only at simulate or checktx | 
| [Link](https://github.com/initia-labs/minievm/pull/168) | F-3 | Burn coins error | 
| [Link](https://github.com/initia-labs/minievm/pull/182) | F-6 | fix: `ConvertCosmosTxToEthereumTx` to properly check type url  | 
| [Link](https://github.com/initia-labs/minievm/pull/171) | F-17 | Use block gas limit in block context | 
| [Link 1](https://github.com/initia-labs/initia/pull/349/commits/16b436610b8d3d12d01f2743efb4961289f30c91), [Link 2](https://github.com/initia-labs/miniwasm/pull/97/commits/8bf9c2bdeeb009adbb09b59d1555ba21c5433c18), [Link 3](https://github.com/initia-labs/minievm/pull/165/commits/68d4c52b6ce4571e353b7811774e41038dd120ad) | F-19 | Fix amino  | 
| [Link](https://github.com/initia-labs/minievm/commit/3650a360d88896a29ddcdee6f2d9060847e6349b) | F-26 | Add salt range check | 
| [Link](https://github.com/initia-labs/miniwasm/pull/97/commits/5a0b2418c29622d991a11e4949019629ee53d54f) | F-1 | Delete cosmwasm address validation | 
| [Link](https://github.com/initia-labs/initia/commit/eb230d9cfd3f60ee3e0ecbd3b1874f12f382b7b9) | F-112 | Fix to return final version | 
| [Link](https://github.com/initia-labs/initia/pull/354/commits/c43ab685be92f6fb222416d18f29ec22f1a698c0) | F-61 | Use quo truncate at distribution pool fraction calculation | 
| [Link](https://github.com/initia-labs/minievm/pull/165/commits/9ebf34cd1aab62b659aa0129c205383ba70b1b4f#diff-adef48e8d5e473dc2b37518579db1a3b7222e0ed0c7ed8a12ae0142f63488321) | F-15 | Apply Ottersec audit | 

**Note:** test files are out of scope

## Out of Scope

- [F-14: Contract deployment restriction can be bypassed](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-14)
- [F-16: `COINBASE` opcode returns an empty address instead of the block proposer resulting in incompatibility with the EVM](https://code4rena.com/evaluate/2025-02-initia-cosmos/findings/F-16)
