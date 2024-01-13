starkli deploy 0x2f8546768eba541ddfa4fedd99084dd80e3a337c8ebf774e3863f1c242b9ecd 0x003796c0679db3cdaDC19Db245b330e943415117b06A8052be46dfC49F5350D5
Enter keystore password: 
Deploying class 0x02f8546768eba541ddfa4fedd99084dd80e3a337c8ebf774e3863f1c242b9ecd with salt 0x03d27a7c1bac091941bda12d98d2e0ab65b79324eade0ebeee5f2e1a7f2644cf...
The contract will be deployed at address 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e
Contract deployment transaction: 0x04785b8f77940844b665a3a3d1299294df855ce488800ba2b425902629539391
Contract deployed:
0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e read_owner
[
    "0x003796c0679db3cdadc19db245b330e943415117b06a8052be46dfc49f5350d5"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % source .env
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli deploy 0x2f8546768eba541ddfa4fedd99084dd80e3a337c8ebf774e3863f1c242b9ecd 0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf
Enter keystore password: 
Deploying class 0x02f8546768eba541ddfa4fedd99084dd80e3a337c8ebf774e3863f1c242b9ecd with salt 0x06fafe4ec3381cfa0d11507a73d1e4f41921a457fe7a48a817b01c048b24514c...
The contract will be deployed at address 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532
Contract deployment transaction: 0x02c997b44fd2816c5b40ff4f15973a8f759592b49670fff7c17a7274972fd3e0
Contract deployed:
0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532 read_owner
[
    "0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % source .env
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e read_owner
[
    "0x003796c0679db3cdadc19db245b330e943415117b06a8052be46dfc49f5350d5"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli invoke 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e transfer_ownership 0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf
Enter keystore password: 
Invoke transaction: 0x000c69f90fc86d51dd22836813b740132a90c646d3c3509b6a2aa17fbad8035f
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e read_owner
[
    "0x047333dacb25b076c21280c2ef4ba76b6f8d14b88892a4cd8c9abf670afc10cf"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e get_data 
[
    "0x0000000000000000000000000000000000000000000000000000000000000000"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli invoke 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e set_data 1234
Enter keystore password: 
Error: code=ContractError, message="Contract error"
(base) ygg@MacBook-Air-2 Ownable-Starknet % source .env
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli invoke 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e set_data 1234
Enter keystore password: 
Invoke transaction: 0x06155dd6f635b7ce8147f0a220de0f7d30648e52a9a338d328d188b4dca27ef7
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli invoke 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532 set_data 0x123456
Enter keystore password: 
Invoke transaction: 0x04f9c15d68c7d5f17b347f424f7a5e25853d738a7a08c64b3e73817ae578a19a
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532 get_data    
[
    "0x0000000000000000000000000000000000000000000000000000000000123456"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e get_data
[
    "0x00000000000000000000000000000000000000000000000000000000000004d2"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e other_func 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532
[
    "0x0000000000000000000000000000000000000000000000000000000000123456"
]
(base) ygg@MacBook-Air-2 Ownable-Starknet % starkli call 0x04763016693211ab9fb6f6041b1550d5d4c7426a24fcee98cba31ac31a193532 other_func 0x05de0a81c27303278e690f015e23bb5d037160ab0772ed38385f9dd2ad13928e
[
    "0x00000000000000000000000000000000000000000000000000000000000004d2"
]