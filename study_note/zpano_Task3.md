# 任务 3

1. 基于 [Ownable contract with SnFoundry](https://github.com/gianalarcon/Ownable-contract-snFoundry)， 在 **tests/test_ownable.cairo** 文件上完成测试。当前包含一个老版本的测试，需要升级到 v0.12.0 or v0.13.0并修复错误，所有的测试必须通过 `snforge test` ，你可参考 [Voting contract](https://github.com/gianalarcon/vote-contract) ，也可查看snfoundry-book 。
2. 部署到测试，并与 [Ownable components](https://github.com/gianalarcon/ownable-components) 合约交互

# 安装`snforge`

通过简单的搜索找到 [snforge](https://foundry-rs.github.io/starknet-foundry/) 的文档

```shell
curl -L https://raw.githubusercontent.com/foundry-rs/starknet-foundry/master/scripts/install.sh | sh
snfoundryup -v 0.12.0
snforge --version
snforge 0.12.0
```

# 修复测试

测试一下

```shell
snforge test
error: no such command: `snforge-test-collector`
[ERROR] Failed to build test artifacts with Scarb
```

说明 Scarb 构建不通过，尝试运行 `scarb build --test` 来看是否有更多的报错信息

![1.png](https://s2.loli.net/2023/12/23/Age8hVPqvsMWpKy.png)

使用文档检索一下相关用法，发现解决方案

[修复io错误](https://foundry-rs.github.io/starknet-foundry/appendix/snforge-library/fs/read_txt.html?highlight=FileTrait#read_txt)

[修复contract_address错误](https://foundry-rs.github.io/starknet-foundry/appendix/cheatcodes/start_prank.html?highlight=start_prank#start_prank)

修改后，通过编译

```shell
scarb build --test
   Compiling test(ownable_starknet_unittest) ownable_starknet v0.1.0 (/Users/zpan/study/starknet/Ownable-contract-snFoundry/Scarb.toml)
   Compiling test(ownable_starknet_test_ownable) ownable_starknet_test_ownable v0.1.0 (/Users/zpan/study/starknet/Ownable-contract-snFoundry/Scarb.toml)
    Finished release target(s) in 2 seconds
```

依旧显示 Scarb 构建不通过
 翻阅文档发现漏了初始化的东西

[Using snforge With Existing Scarb Projects](https://foundry-rs.github.io/starknet-foundry/getting-started/first-steps.html)

```shell
scarb add snforge_std \
 --git https://github.com/foundry-rs/starknet-foundry.git \
 --tag v0.12.0
```

![1.png](https://s2.loli.net/2023/12/23/Age8hVPqvsMWpKy.png)

# 部署合约以及交互

```shell
scarb build
starkli declare  target/dev/ownable_starknet_ownable.contract_class.json
starkli deploy 0x0585f86478c05aab66a1cb29496dfdb84fe8729a170a46f010af95574a1e5d5c 0x02b2297b35f2fabdc21ab68f5646c41b3cf4fe3056a9aba8a34425c9f2830088
starkli invoke 0x01b0ea55a9ed11ce67896399013c469282c2d15775c018066cf07181bae02322 set_data
```