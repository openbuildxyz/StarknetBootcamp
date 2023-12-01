# 如何部署 Cairo 到测试网

## 安装 Starkli

 Starkli 是用来和 Starknet 网络 (包括本地网络) 进行交互的命令行工具。

 Starkli 提供了一个名为 starkliup 的软件包管理器，允许获取并安装最新发布的二进制文件。类似于 Rust，其中 rustup 用于安装、管理和升级 rustc。

安装 starkliup：

```
curl https://get.starkli.sh | sh
```



按安装提示将 `starkliup`  加入到环境变量中（），使用  `starkliup` 安装 `starkli` ， 命令如下：

```
starkliup
```



稍等一会后，starkli 就可以在我们的终端中使用。

```
starkli --version
0.1.20 (e4d2307)
```



## 准备钱包

在链上部署合约，我们需要钱包账号来支付 Gas 费，因此需要我们有一个可使用的账户。

大家可以选择  [Braavos](https://braavos.app/)、[ArgentX](https://www.argent.xyz/argent-x/) ， 他们都有浏览器插件版本，操作方法可 MetaMask 类似，按提示创建钱包即可。并从[官方水龙头](https://faucet.goerli.starknet.io/)重获取一些 ETH 。



在 Starknet 上的钱包账户都是智能合约，刚在钱包创建好后，我们看到的地址还是一个反事情地址（没有在链上实际存在），在发起第一次发起交易时将自动部署钱包合约。



在 Starknet 中，对于每个智能钱包，有两个部分来控制：**一个签名者（signer）**和**一个帐户描述**。

和以太坊上大家常用的 EOA 钱包不同， EOA 钱包由节点中验证签名，只支持一个私钥（或助记词、Keystore 文件）签名来管理账户。

智能钱包在合约中验签，可以支持多种签名方式（签名者），帐户描述则是用来描述签名与智能钱包账户的关系。



### 创建 signer



先创建一个名为 .`wallets` 的新文件夹来存储智能钱包所需的文件。

```
mkdir .wallets
```

签名者（**signer**）可以是一个私钥或者是一个加密的`keystore` ，为避免明文暴露私钥，通常选择后者。

我们可以从 Braavos 或 ArgentX 导出的私钥来创建 `keystore`：

```
> starkli signer keystore from-key .wallets/keystore.json
Enter private key:
Enter password:
Created new encrypted keystore file: /Users/emmett/CairoProject/ownable/.wallets/keystore.json
Public key: 0x075ce30939a0f44df2dbad6f24d1e82200a1ee084a387afc1bc657aba61f441b
```

该命令让我们输入私钥已经密码，私钥可以从钱包导出，如下图：



![image-20231130160723074](https://img.learnblockchain.cn/pics/20231130160724.png)

之后就会生成 `.wallets/keystore.json`， 使用 Starkli 发起交易时，Starkli 就可以使用 keystore 来签名交易了。



### 创建帐户描述



如果在Starknet 上已经存在该账户，可以使用 `starkli account fetch`  获取账户信息来创建帐户描述文件：

```
starkli account fetch 0x0325E8b88aedBac03c5dc9E22bF94d47E6508f9723FD085f5D7b5809afA48bC4 --output .wallets/account.json --rpc https://starknet-goerli.g.alchemy.com/v2/xxxxxxx
```

`--output`  指定输出帐户描述文件位置。

`--rpc` 指定节点 RPC ，这里使用的是 [Alchemy](https://alchemy.com/?r=7d60e34c-b30a-4ffa-89d4-3c4efea4e14b) 的节点 RPC  。



如果账户没有在链上部署，你会遇到如下错误：

```
Error: code=ContractNotFound, message="Contract not found"
```

可以在钱包上执行一笔转账交易，这时会自动创建好该钱包账户。



## 声明合约（`declare` ）



在以太坊上，可以直接把 Solidity 合约部署到网络上，Starknet 分成了两个部分，先发布合约代码（编译生成的中间表示），再用合约代码创建合约实例。

第一部分称为：声明（`declare`）合约， 第二部分成为部署合约。



声明合约需要发起交易，方便起见，先把发起交易需要的账号及 RPC 写入到环境变量中：

创建文件：`envsh` :

```
export STARKNET_RPC="https://starknet-goerli.g.alchemy.com/v2/replace_with_your_key"
export STARKNET_ACCOUNT=".wallets/account.json"
export STARKNET_KEYSTORE=".wallets/keystore.json"
```

请在环境变量中使用你的 RPC key 及 账号文件。 命令行中使用 `source envsh` 应用上环境变量。



使用 `starkli declare`  命令声明合约（将自动使用以上环境变量）：

```
> starkli declare target/dev/ownable_ownable.contract_class.json
Enter keystore password:
Sierra compiler version not specified. Attempting to automatically decide version to use...
Network detected: goerli-1. Using the default compiler version for this network: 2.1.0. Use the --compiler-version flag to choose a different version.
Declaring Cairo 1 class: 0x077bd1a78e208a5e73995278e4300066fa14259f48c33123fe0de13bf8b8a24d
Compiling Sierra class to CASM with compiler version 2.1.0...
CASM class hash: 0x047ddccc9bd2effa6fd847b5338c59e629aab644fa847dc1ff4dfc9d37c2a318
Contract declaration transaction: 0x01c1bc0f998f237d4ebdb3a4e7f0ff4973fc6b9b1a1d1c2ea9832865c439b8df
Class hash declared:
0x077bd1a78e208a5e73995278e4300066fa14259f48c33123fe0de13bf8b8a24d
```



命令中的 `ownable_ownable.contract_class.json`  是 `scarb build` 生成的文件。

声明合约成功后，会获取到一个 class hash 。



## 部署合约

部署合约使用命令：`starkli deploy  class_hash  [参数]` ， 因此：

```
starkli deploy 0x077bd1a78e208a5e73995278e4300066fa14259f48c33123fe0de13bf8b8a24d 0x0325E8b88aedBac03c5dc9E22bF94d47E6508f9723FD085f5D7b5809afA48bC4
```

若无错误，会有类似以下返回：

```
Deploying class 0x077bd1a78e208a5e73995278e4300066fa14259f48c33123fe0de13bf8b8a24d with salt 0x0633b1c1d0cbedc9f5cd924115b1dad08718d1c39fc53bc54da9d667b09a99af...
The contract will be deployed at address 0x03264b6bdb740c14b776972ce2065c4b79cc6002fb0438ade0bb480c4774b272
Contract deployment transaction: 0x013eaf1be2782413ded7049b48da459d9f41c3a3d68b69da7b38a2d2c3b84a8d
Contract deployed:
0x03264b6bdb740c14b776972ce2065c4b79cc6002fb0438ade0bb480c4774b272
```

也可以在 starkscan 浏览器上查看到该合约：

https://testnet.starkscan.co/contract/0x03264b6bdb740c14b776972ce2065c4b79cc6002fb0438ade0bb480c4774b272#overview



## 调用合约

与合约交互有两个方法：call 和 invoke.

call 用于读方法，invoke 用于向合约写入数据。



现在，我们调用一下合约的 get_owner 方法：

```
starkli call 0x03264b6bdb740c14b776972ce2065c4b79cc6002fb0438ade0bb480c4774b272 get_owner
```



返回：

```
[
    "0x0325e8b88aedbac03c5dc9e22bf94d47e6508f9723fd085f5d7b5809afa48bc4"
]
```



也可以在浏览器中调用合约。

https://testnet.starkscan.co/contract/0x03264b6bdb740c14b776972ce2065c4b79cc6002fb0438ade0bb480c4774b272#read-write-contract


