 Starknet 是以太坊的二层 ZKRollup 扩容方案 ，和其他兼容EVM 的二层扩容方案不同， Starknet 上开发有自己的模式。

我们从一个简单的对比角度，方便 Solidity 智能开发者快速理解 Starknet 开发。



## 开发语言 Cairo vs Solidity



Solidity 是一个为 EVM 设计的语言，语法类似 Python 与 JavaScript ，以太坊执行客户端为了验证一致性，所有的调用合约的交易会在各个节点上重新执行，以检查时候运行的结果一样。



Starknet 使用开发语言 Cairo ， Cairo 是一种写可证明的程序语言， 用Cairo编写的程序，会生成**证明**（不需要用户了解ZK知识 ），可证明结果是由特定的程序和特定的输入得到，而不用重复运行程序（从而可以节约大量重复运营的开销，达到扩容）。



Cairo 是一个通用的可证明的程序语言，除在 Starknet 中使用之外，可广泛使用在其他的场景中。

Cairo 运行于 CairoVM 之上，是类 Rust 语言，和 Rust 有类似的所有权模型，入门门槛有点高，Cairo 语言学习中文用户可参考 [StarknetAstro](https://starknet-astro.super.site/) 翻译的 [Cairo 之书](https://book.cairo-lang.org/zh-cn/index.html) 。



## 账户

在 EVM 中，有两类账户： EOA（外部账号） 和 合约账户 ，用户通常使用 MetaMask 等钱包来管理外部账户。



在 Starknet 中，原生支持账户抽象（AA），所有的账户是智能合约，使用合约验证交易，支持多种验签方式，以及支持社交恢复、批量交易等。 使用的钱包主要是  [Braavos](https://braavos.app/)、[ArgentX](https://www.argent.xyz/argent-x/)



## 项目管理工具

Solidity 项目通常使用 Foundry 或 Hardhat 开发。

Cairo 使用 scarb： Scarb是Cairo语言的项目管理工具。 集成包管理器和编译器，Scarb 可管理依赖项，编译Cairo项目。



scarb 安装： 

```bash
curl --proto '=https' --tlsv1.2 -sSf https://docs.swmansion.com/scarb/install.sh | sh
```





浏览器：starkscan 、Voyager



https://github.com/glihm/starknet-basecamp-7/tree/main/demo

https://github.com/starknet-edu/starknet-cairo-101/blob/main/README.zh.md



## 第一个 Cairo 合约

scarb 安装后，可以创建项目了， 我们第一个 Cairo 合约为 `Ownable` ：

```
scarb new ownable
```

其结构如下：

```
   src/
      lib.cairo
    .gitignore
    Scarb.toml
```



### Scarb.toml

`Scarb.toml` 是项目的清单文件（Manifest），包含了编译该项目的元数据，将以下内容复制到`Scarb.toml` 文件：

```toml
[package]
name = "ownable"
version = "0.1.0"

[dependencies]
starknet = ">=2.2.0"


[[target.starknet-contract]]
sierra = true
```



`Scarb.toml` 中的第一部分是 `[package]` ，定义项目软件包，包含字段 `name` 和 `version` 。

`dependencies` 定义库依赖项，我们的合约需要依赖官方库：`starknet`。

`target` 定义编译目标，使用`.starknet-contract` ，这里目标中间语言 `sierra` 。



`Scarb.toml`  更多键值定义可参考：https://docs.swmansion.com/scarb/docs/reference/manifest.html



### Cairo 合约代码

Starknet 合约实际上是一个 Cairo module ，我们用一下代码替换掉 `lib.cairo` 中的代码： 

```caico
#[starknet::contract]
mod ownable {

    use starknet::ContractAddress;

    #[storage]
    struct Storage {
        owner: ContractAddress,
    }

    #[constructor]
    fn constructor(ref self: ContractState,
        init_owner: ContractAddress ) {
            self.owner.write(init_owner);
        }


    #[external(v0)]
    fn get_owner(self: @ContractState) -> ContractAddress {
        self.owner.read()
    }
}
```

在这段合约代码中使用了一些宏（ `#` 开头）来定义合约、定义存储、定义构成函数及外部函数

> 宏是一个稍微复杂一点的概念，我们只要知道，其是在编译阶段用来对代码进行扩展。



### 编译

使用命令：

```scarb build
scarb build
```

如果代码没有问题，将有以下类似的输出：

 ```
   Compiling ownable v0.1.0 (/Users/emmett/CairoProject/ownable/Scarb.toml)
    Finished release target(s) in 1 second
 ```



编译会在 `target/dev/` 下生成一个编译后的文件：`ownable.starknet_artifacts.json` 及 `ownable_ownable.contract_class.json`

在这里，合约就准备好了。

接下来看看如何部署的 Starknet 网络中去。