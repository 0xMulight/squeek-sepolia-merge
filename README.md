# Squeek Sepolia 一键合成

公开小工具：在 Sepolia 上调用官方 `SqueekNFT.merge(survivor, donor)`，用自己的钱包签名完成合成。

**在线页面：** https://0xmulight.github.io/squeek-sepolia-merge/

## 做什么

- 连接 OKX / MetaMask（或其他注入 `window.ethereum` 的钱包）
- 自动切到 Sepolia（chainId `11155111`）
- 填写要留下的 survivor ID、要烧掉的 donor ID
- 发送一笔 `value = 0` 的 `merge` 交易到官方 NFT 合约

合约地址（固定写死在页面里）：

`0xC4C7982657f00509548F3a3a41db7FA439a6856B`

## 别人怎么用

1. 打开上面的在线页面  
2. 连接**自己的**钱包，网络选 Sepolia  
3. 填入**自己的**两个 NFT 编号（同等级）  
4. 点「合成」，在钱包弹窗里核对：`to` 必须是上面的合约、金额为 0，再确认  

页面里的「5427 / 5428」「5429 / 5430」只是示例快捷填入，别人请改成自己的编号。

## 合成前请确认

- 两个 NFT 都在你当前连接的钱包里  
- 等级相同，且都已过 merge 冷却（Level 1 无冷却；升到 L2 后约需 3000 个已完成 Squeek 块才能再合）  
- donor 会**永久烧掉**，不可撤销  
- 官方需已开启 merges（`mergesOpen`）

## 安全说明

- 源码全部在本仓库的 `index.html`，无外挂脚本、无后端  
- 不请求 `approve`、不转 ETH / 其他代币、不读取助记词或私钥  
- 私钥始终在你的钱包里；网页只能发起交易请求，最终由你在钱包确认  
- 公开仓库任何人都能看和 fork；**只有仓库所有者（或被添加写权限的人）才能改线上页**。合并陌生 PR、泄漏 GitHub 账号前请想清楚  

## 本地打开

把 `index.html` 用浏览器打开，或任意静态托管即可。需要已安装钱包扩展。

## 免责

这是社区便利页，不是 Squeekchain 官方产品。合约规则以 [Squeekchain Docs](https://docs.squeekchain.com/) 为准。用前自己核对合约地址与钱包弹窗。

## Stake

One-click deposit page (Sepolia): [stake.html](./stake.html) · live: https://0xmulight.github.io/squeek-sepolia-merge/stake.html

Calls only `SqueekStaking.deposit` / optional `setApprovalForAll` on the official NFT. No approve-unlimited ERC20, no ETH transfer.
