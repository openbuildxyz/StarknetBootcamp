# Starknet Bootcamp

[English](./README.md) / [中文](./README_zh.md)

一起学习 Cairo， 为可验证未来添砖加瓦。



## Starknet Basecamp VII 【英文】

1. [Youtube 视频播放列表](https://www.youtube.com/playlist?list=PLMXIoXErTTYX-ZSxlaYDxsR66l5a39IwA)
2. 课件：
   1.  [基础知识](https://docs.google.com/presentation/d/1hlDYWmNX5j2UUZsXLvDLb1kR8rwPvjAnbpfo3hg_kEU/edit#slide=id.g25b027f2396_0_0) 
   2. Cairo 练习: https://github.com/shramee/starklings-cairo1
   3. [ Starknet](https://docs.google.com/presentation/d/1NCBlO-9kdF1t54kR9Q7cvSAGoC2PocTrlr4SryAeBmU/edit#slide=id.g1dff4c31abe_0_50)
   4. [ 测试](https://docs.google.com/presentation/d/1KSI_8rcxvxXJU-oeKngj_s5T_RNdKPSs7h-_jONWBA4/edit?usp=sharing)
   5.  [前端](https://docs.google.com/presentation/d/1Q5HnlJ90QpttAzxweXQe8mAPOZV93tTClJn43Q5UUM0/edit?usp=sharing) 
   6.  [ 架构](https://docs.google.com/presentation/d/1E2J0d_n7TxSnNPHY9watHlUNETYjM5Ad3lke-6-5PPg/edit?usp=sharing)



中文开发者可以试试[这个chrome插件 ](https://chromewebstore.google.com/detail/language-learning-with-ne/bekopgepchoeepdmokgkpkfhegkeohbl?utm_source=ext_app_menu)，可实时显示中英文。

## OpenBuild Starknet Bootcamp【英文】

1. [视频播放列表](https://openbuild.xyz/learn/challenges/89) 更新中...



## Starknet 中文公开课



1. Openbuild 课程 - [视频列表](https://openbuild.xyz/learn/courses/1022180033)

2. B 站[播放列表](https://space.bilibili.com/581611011/channel/collectiondetail?sid=1949923)

   

## 写学习笔记领奖金

如果你在课程中有一些自己的学习笔记，或者搭建了自己的知识库想要分享给更多人，欢迎来到这个开源仓库和我们共学共建～

以下是一个学习笔记的提交示例，在 study_note 下创建自己的笔记名称：你的名字_笔记名.md

将你的内容以 md 文档的格式创建在其中，文档的命名尽量简洁概括，方便其他人进行查阅学习，笔记合并在仓库后，将根据内容质量进行奖励。



笔记 1：[给 Solidity 开发者的 Starknet 开发指南](https://learnblockchain.cn/article/7007) 

笔记 2：[Ownable合约部署、所有权转移、dispatcher交互](https://learnblockchain.cn/article/7093) 



## Bounty 任务

### 任务 1： 完成 [starklings](https://github.com/shramee/starklings-cairo1) 中的练习

总奖金:  $200 ， 完成任务的前 20 名用户

如何提交任务:

1. 为防止女巫攻击，需登录 [OpenBuild](https://openbuild.xyz/) 壁挂炉完善个人资料
2. 克隆练习库： https://github.com/shramee/starklings-cairo1
3. 按照指引完成练习， 可参考[视频](https://www.youtube.com/watch?v=ofyhpQYTycs&list=PLMXIoXErTTYX-ZSxlaYDxsR66l5a39IwA&index=2&t=5608s)。
4. 在 Starknet 交流群中(加群联系微信：xlbxiong，备注 cairo)， 贴出你的练习库 Github 地址。

### 任务 2

基于 [Ownable contract](https://github.com/gianalarcon/Ownable-Starknet/)，在 testnet 上用不同的钱包（argent 和 braavos）部署 2 个智能合约。将合约所有权从 argent 钱包账户转移到 braavos 账户。与 dispatcher 交互，从智能合约 1 调用智能合约 2 的数据。

总奖金: $200 美元，完成任务的前 20 名用户

如何提交：

1. 为避免女巫攻击，您需要登录 [OpenBuild 网站](https://openbuild.xyz/) 并填写个人资料。
2. 完成任务2，可以先学习[视频](https://www.youtube.com/watch?v=6oSHviHTTOo&list=PLMXIoXErTTYX-ZSxlaYDxsR66l5a39IwA&index=3) 和这个[笔记文章](https://learnblockchain.cn/article/7007).
3. 在 Starknet 交流群中(加群联系微信：xlbxiong，备注 cairo)， 贴出你的部署合约的地址。



### 任务 3

1. 基于 [Ownable contract with SnFoundry](https://github.com/gianalarcon/Ownable-contract-snFoundry)， 在 **tests/test_ownable.cairo** 文件上完成测试。当前包含一个老版本的测试，需要升级到 v0.12.0 or v0.13.0并修复错误，所有的测试必须通过 `snforge test` ，你可参考 [Voting contract](https://github.com/gianalarcon/vote-contract) ，也可查看snfoundry-book 。

2. 部署到测试，并与 [Ownable components](https://github.com/gianalarcon/ownable-components)  合约交互

总奖金: $100 美元，完成任务的前 10 名用户



**如何提交**: 

完成任务 3前需先完成任务 1 和任务 2，在 Starknet 交流群中(加群联系微信：xlbxiong，备注 cairo)，贴出 github 地址及合约地址及测试完成截图。



### 任务 4

基于dojo-starter项目,  使用 **Slot** 命令部署游戏，可以参考这个 [教程](https://book.dojoengine.org/tutorial/deploy-using-slot/main.html)。 你需要为 katana slot 和  torii slot 提供 RPC 节点 URL， 部署的 katana 和 torii slot 名必须和github 用户一致。例如：

1. Katana rpc: https://api.cartridge.gg/x/**github-username**/katana
2. Torii 端点
   1. GraphQL: https://api.cartridge.gg/x/**github-username**/torii/graphql
   2. GRPC: [https://api.cartridge.gg/x/**github-username**/torii/grpc](https://api.cartridge.gg/x/github-username/torii/grpc)

参考文档：

- https://book.dojoengine.org/toolchain/slot/overview.html 
- https://github.com/cartridge-gg/slot 



总奖金: $100 美元，完成任务的前 10 名用户



**如何提交**: 

完成任务 4 前需先完成任务 3，在 Starknet 交流群中(加群联系微信：xlbxiong，备注 cairo)，贴出 github 地址及合约地址及测试完成截图。






## Resources/学习资料

### Docs/文档：

1. [The Starknet Book](https://book.starknet.io/)

2. [Starknet Docs](https://docs.starknet.io/documentation/)

3. [Cairo book](https://book.cairo-lang.org/) / [中文版](https://book.cairo-lang.org/zh-cn/index.html)

4. Reddio 整理的 [Hackathon Guide: A to ZK](https://reddio.notion.site/reddio/Hackathon-Guide-A-to-ZK-fd66f91a555941c7a05d2680bbd6f234)

   

## 合约示例

1. [Cairo-by-example](https://cairo-by-example.com/)
2. [Starknet-by-example](https://starknet-by-example.voyager.online/)
3. [OpenZeppelin Cairo](https://github.com/OpenZeppelin/cairo-contracts/)
4. [Reddio Cairo templates](https://github.com/reddio-com/cairo)



