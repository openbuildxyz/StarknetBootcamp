# How to commit tasks

1. snforge test
```
snforge test  

    Finished release target(s) in 3 seconds


Collected 4 test(s) from task_3 package
Running 0 test(s) from src/
Running 4 test(s) from tests/
[PASS] tests::test_ownable::test_transfer_ownership_bad_guy (gas: ~4291)
[PASS] tests::test_ownable::test_construct_with_admin (gas: ~4292)
[PASS] tests::test_ownable::test_data_mock_call_get_data (gas: ~4298)
[PASS] tests::test_ownable::test_transfer_ownership (gas: ~4298)
Tests: 4 passed, 0 failed, 0 skipped, 0 ignored, 0 filtered out
```
2. declare & deploy  other_contract.cairo
```
starkli declare .\target\dev\task_3_ownable_contract.contract_class.json

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Sierra compiler version not specified. Attempting to automatically decide version to use...
Network detected: goerli. Using the default compiler version for this network: 2.4.0. Use the --compiler-version flag to choose a different version.
Declaring Cairo 1 class: 0x06facc60a74ebd9d683c60e2edbe8780fe2630924e1f3dcf694a9418e2c9d7d2
Compiling Sierra class to CASM with compiler version 2.4.0...
CASM class hash: 0x00bec2e19ce9af001758e96dbd2b41d6917c214a607be022320d206bf780293f
Contract declaration transaction: 0x048064631cff567ecb9c50e96c5652457cba189048473b923fa0f9929a0f2e03
Class hash declared:
0x06facc60a74ebd9d683c60e2edbe8780fe2630924e1f3dcf694a9418e2c9d7d2

starkli deploy 0x06facc60a74ebd9d683c60e2edbe8780fe2630924e1f3dcf694a9418e2c9d7d2 
0x00923f26b243f57b591183cc769184f43ea97c8ed7c5c2f40897dd89c967cde5

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Deploying class 0x06facc60a74ebd9d683c60e2edbe8780fe2630924e1f3dcf694a9418e2c9d7d2 with salt 0x0360aa2e162bd2170ba62c25a3af5311b898190f44204acd6253e90f9184cac1...
The contract will be deployed at address 0x07e6e28295dc0d481c29758332e17060a60cd42d5f22a9a0d79b5de7950097b5
Contract deployment transaction: 0x06fcc66fcd39bb172bf403ae9a12585602274befb8ab4e770fff5a8e8330bc84
Contract deployed:
0x07e6e28295dc0d481c29758332e17060a60cd42d5f22a9a0d79b5de7950097b5
```

3. declare & deploy ownable.cairo
```
starkli declare .\target\dev\task_3_ownable.contract_class.json

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Sierra compiler version not specified. Attempting to automatically decide version to use...
Network detected: goerli. Using the default compiler version for this network: 2.4.0. Use the --compiler-version flag to choose a different version.
Declaring Cairo 1 class: 0x0287a5387cdf8119d7844fe110e35384ab28296d2ac4894d6c73baf95aeade5b
Compiling Sierra class to CASM with compiler version 2.4.0...
CASM class hash: 0x01cf30830a36b80f72e5a6da74186f5a9ffcee82806307c5be8316881dd4598c
Contract declaration transaction: 0x01d45e2d5e64b9dbf2716b5862cdea2e732c37ba181c72738ca5eefd8d049e0b
Class hash declared:
0x0287a5387cdf8119d7844fe110e35384ab28296d2ac4894d6c73baf95aeade5b

starkli deploy 0x0287a5387cdf8119d7844fe110e35384ab28296d2ac4894d6c73baf95aeade5b 0x00923f26b243f57b591183cc769184f43ea97c8ed7c5c2f40897dd89c967cde5
WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Deploying class 0x0287a5387cdf8119d7844fe110e35384ab28296d2ac4894d6c73baf95aeade5b with salt 0x0279b49b991f6aed2b617712e9057efbde1fae21e0bc1eaf56845b60b17ac969...
The contract will be deployed at address 0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd
Contract deployment transaction: 0x03015ae1fba8ec40ad2b0e921fca866b444d43c08b0bc73ac5ade4ecc7947ddd
Contract deployed:
0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd

```
4. ownable.cairo调用
```
starkli call 0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd get_data

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
[
    "0x0000000000000000000000000000000000000000000000000000000000000001"
]


starkli invoke 0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd set_data 0xa

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
Enter keystore password:
Invoke transaction: 0x072f8d7fcdd442570edefc57ca599783a01ac9ca8cfc678e54bee7721147cb4b

starkli call 0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd get_data

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
[
    "0x000000000000000000000000000000000000000000000000000000000000000a"
]
```

5. ownable.cairo调用other_contract.cairo
```
starkli call 0x007d031ab2d3358ee880a83345ce1ca4d8cf619ad88ae97f061eb51faf1241fd other_func 0x07e6e28295dc0d481c29758332e17060a60cd42d5f22a9a0d79b5de7950097b5

WARNING: you're using neither --rpc (STARKNET_RPC) nor --network (STARKNET_NETWORK). The `goerli` network is used by default. See https://book.starkli.rs/providers for more details.
[
    "0x0000000000000000000000000000000000000000000000000000000000000001"
]
```
