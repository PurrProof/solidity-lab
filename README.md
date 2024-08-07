## Ethernaut Game: https://ethernaut.openzeppelin.com/

### CoinFlip level https://ethernaut.openzeppelin.com/level/0x6765a87878A413E0dEDEaAD34fbD8342a4300c56

Set up your `.env` file with:

```plaintext
ETH_RPC_URL=https://ethereum-holesky-rpc.publicnode.com
RAW_PRIVATE_KEY=your_private_key_here
COINFLIP_INSTANCE=address_of_the_CoinFlip_contract
COINFLIPGUESSER_INSTANCE=address_of_the_CoinFlipGuesser_contract
```

Deploy the CoinFlipGuesser Contract: `pnpm dotenv pnpm ethernaut:coinflip:deploy`

See wins count: `pnpm dotenv pnpm ethernaut:coinflip:wins`

Make a Guess 10 times: `pnpm dotenv pnpm ethernaut:coinflip:guess`, then continue with Ethernaut console.

### Telephone level https://ethernaut.openzeppelin.com/level/0x9D8e38b52F08FD7b0fc5C04460CdFC3AC30ce7bf

```plaintext
TELEPHONE_INSTANCE=address_of_the_Telephone_contract
TELEPHONE_PROXY_INSTANCE=address_of_the_TelephoneProxy_contract
```

Deploy the TelephoneProxy Contract: `pnpm dotenv pnpm ethernaut:telephone:deploy`

See Telephone owner: `pnpm dotenv pnpm ethernaut:telephone:owner`

Change owner: `pnpm dotenv pnpm ethernaut:telephone:own`, then continue with Ethernaut console.

### Token balance level https://ethernaut.openzeppelin.com/level/0x7AE87cf24Fb5096182a969a1Ad45D0c54410d1Ca

You'll need

```plaintext
PLAYER_ADDRESS=0x...
TOKEN_INSTANCE=0x...
```

- Check player balance: `pnpm dotenv pnpm ethernaut:token:balance`
- Transfer balance (because of underflow) `pnpm dotenv pnpm ethernaut:token:transfer` (you may need to change transfer value in script, it should be more for a 1 than player balance)

### Delegation level https://ethernaut.openzeppelin.com/level/0xF695A9661A3b909ffb15F97556bAb286b19520E7

Execute following command in console: `await sendTransaction({from:player, to:contract.address, data: "0xdd365b8b", gas:300000})`. `0xdd365b8b` is a signature of `pwn()` function. This function call will be delegated to the Delegate contract, and be executed in the context of the Delegation contract. So `owner` storage variable of the Delegation contract will ve changed to `msg.sender`.

### Force level https://ethernaut.openzeppelin.com/level/0x4e8Da8e21d27A10BA7d2510cB90338374828bE86

```
FORCE_INSTANCE=0x...
```

- call `pnpm dotenv pnpm ethernaut:forcer:deploy`
- check `await getBalance(contract.address)` in ethernaut console

Force contract have been forced to receive Eth on attacker contract selfdestruct.

### Vault level

- `cast storage -r https://ethereum-holesky-rpc.publicnode.com ...level_address... 1` read slot #1 in storage
- `await contract.unlock("0x...slot contents....");` in browser console

## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

- **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
- **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
- **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
- **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
```
