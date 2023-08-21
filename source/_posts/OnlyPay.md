---
title: OnlyPay（一）
tags:
  - "Golang"
categories:
  - "Golang"
  - "Web3"
---

OnlyPay 是一套 Web3 的企业级多租户跨链支付系统。接下去的工作中，我会从 0-1 来实现它。这个过程中，我会把思路和实现一点点 POST 出来，就像平时做项目一样，也欢迎有兴趣的小伙伴加入！

### 项目链接

> https://github.com/DwGoing/OnlyPay

### 阶段目标

> - [x] HD 钱包管理
>   - [x] 助记词导入
>   - [x] 生成不同类型主链钱包地址
> - [ ] EVM 链原生代币及 ERC20 代币相关操作
>   - [ ] 转账
>   - [ ] 生成接收钱包
>   - [ ] 监控转账及回调
>   - [ ] 资金归集
> - [ ] 用户管理
>   - [ ] 注册
>   - [ ] 生成 Token
>   - [ ] 通过 Token 使用资金服务

### 开发思路

> - 创建项目目录
>   ![](image1.png)

> - hd_wallet [HD 钱包](https://github.com/DwGoing/OnlyPay/tree/main/pkg/hd_wallet)
>   1. HD 钱包的思路就是从助记词中还原 seed，然后通过 seed 获得 Master Key,之后的子钱包就通过这个 Key 加上路径来派生出子钱包私钥；
>   2. 目前先实现 BTC 3 种类型地址生成和 ETH 类型地址生成；

> - fund_service [资金管理服务](https://github.com/DwGoing/OnlyPay/tree/main/internal/service/fund_service)
>   包括注册资金账户，生成助记词，生成收款钱包，监听收款及回调等功能。
>   1. 针对不同类型主链实现不同 Processor，不同类型是指 Bitcoin 类、EVM 类、Move 类等，并应该提供 IProcessor 接口；
