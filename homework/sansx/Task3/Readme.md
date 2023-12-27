# How to test
run `snforge test`

# How to deploy
### 1. Set env
create a env file, add env configs, run 
  `source <Your env file path>`
```
export STARKNET_RPC="https://starknet-goerli.g.alchemy.com/v2/replace_with_your_key"
export STARKNET_ACCOUNT=".wallets/account.json"
export STARKNET_KEYSTORE=".wallets/keystore.json"
```

### 2. build your file
run 
`scarb build`

you'll get files in `target/dev` dir, it will have a file called `ownable_starknet_ownable.contract_class.json`, we need use the path of this file when we deploy 

### 3. declare contract
run 
`starkli declare <Your builded contract json file path>`

it will be `target/dev/ownable_starknet_ownable.contract_class.json`

so, here we run
`starkli declare target/dev/ownable_starknet_ownable.contract_class.json`

we'll get such output after running command:

```
❯ starkli declare target/dev/ownable_starknet_ownable.contract_class.json

Enter keystore password: 
Sierra compiler version not specified. Attempting to automatically decide version to use...
Network detected: goerli. Using the default compiler version for this network: 2.4.0. Use the --compiler-version flag to choose a different version.
Declaring Cairo 1 class: 0x05e70594cbd13a61ea2cfec726b27836ad745e7caf6dc9a68714fdcf7a120c7a
Compiling Sierra class to CASM with compiler version 2.4.0...
CASM class hash: 0x01cf30830a36b80f72e5a6da74186f5a9ffcee82806307c5be8316881dd4598c
Contract declaration transaction: 0x0020645c55c57ed2db396281851ffda1a86851c53b1fef0c4fa1e0bf4e00fdff
Class hash declared:
0x05e70594cbd13a61ea2cfec726b27836ad745e7caf6dc9a68714fdcf7a120c7a
```

### 3. deploy contract
run
`starkli deploy <Class hash declared above> <Params>`

we'll get return like this:
```
❯ starkli deploy 0x05e70594cbd13a61ea2cfec726b27836ad745e7caf6dc9a68714fdcf7a120c7a <Your wallet address>

Enter keystore password: 
Deploying class 0x05e70594cbd13a61ea2cfec726b27836ad745e7caf6dc9a68714fdcf7a120c7a with salt 0x0536a3630ea80636d6e64927fdb8b417f35b3d6e724b6b617036de389ba416fd...
The contract will be deployed at address 0x03e07be975c507ae60d5be9dd32b2ad396c3b36ca707091dca3ee23a5f1f6e77
Contract deployment transaction: 0x064a8034cb29b3afb2a60df060898711d6f219fde38e5442db24479610a7fb67
Contract deployed:
0x03e07be975c507ae60d5be9dd32b2ad396c3b36ca707091dca3ee23a5f1f6e77
```
