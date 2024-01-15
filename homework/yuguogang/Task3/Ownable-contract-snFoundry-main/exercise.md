(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % starkli deploy 0x0585f86478c05aab66a1cb29496dfdb84fe8729a170a46f010af95574a1e5d5c 0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf
Enter keystore password: 
Deploying class 0x0585f86478c05aab66a1cb29496dfdb84fe8729a170a46f010af95574a1e5d5c with salt 0x071f4320daee49a059c10d0b2bcd2cd03d641ca9d9491e574c8d84282afe382a...
The contract will be deployed at address 0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3
Contract deployment transaction: 0x067f6c991b14546b5897885d6f528276856d904357b8c161e7e59d9c688e8259
Contract deployed:
0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % starkl
i call 0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3 read_owner
[
    "0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf"
]
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % starkli call 0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3 get_data  
[
    "0x0000000000000000000000000000000000000000000000000000000000000001"
]
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % starkli invoke 0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3 set_data 0x12345
Enter keystore password: 
Invoke transaction: 0x0413043072141ceab23402c0363f98cb8e6bf96947f98a16cdcc31e5bec19628
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % starkli call 0x07e7a4eb1d63354f67bb88b07556688817b86a85b5048660b3fc93375fc2edd3 get_data 
[
    "0x0000000000000000000000000000000000000000000000000000000000012345"
]
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % snforge test
   Compiling ownable_starknet v0.1.0 (/Users/ygg/vs/StarknetBootcamp/homework/yuguogang/Task3/Ownable-contract-snFoundry-main/Scarb.toml)
    Finished release target(s) in 2 seconds


Collected 4 test(s) from ownable_starknet package
Running 0 test(s) from src/
Running 4 test(s) from tests/
[PASS] tests::test_ownable::test_transfer_ownership, gas: ~13.71
[PASS] tests::test_ownable::test_transfer_ownership_bad_guy, gas: ~6.2
[PASS] tests::test_ownable::test_construct_with_admin, gas: ~7.140000000000001
[PASS] tests::test_ownable::test_data_mock_call_get_data, gas: ~13.32
Tests: 4 passed, 0 failed, 0 skipped, 0 ignored, 0 filtered out
(base) ygg@MacBook-Air-2 Ownable-contract-snFoundry-main % 