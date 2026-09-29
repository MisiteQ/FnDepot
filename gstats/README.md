# GStats

飞牛 fnOS 上的 GitHub 仓库流量统计平台（FPK 原生应用）：通过 GitHub 官方 Repo Traffic API 统计仓库**外部访客**的浏览量（PV）、独立访客（UV）、克隆次数、来源网站与热门路径，每日自动快照存档，突破 GitHub 仅保留 14 天数据的限制。所有数据仅保存在 NAS 本机，不上传第三方服务器。

## ✨ 功能

- **流量统计**：仓库维度 / 每日维度的 PV、UV、克隆次数与去重克隆者数，概览页双系列柱状图、仓库浏览 TOP10、来源网站 TOP10
- **自动同步**：绑定账号 3 秒后自动同步一次，服务启动 45 秒后、之后每 6 小时全量同步，也可在概览页手动触发
- **长期存档**：GitHub 官方只保留近 14 天数据，GStats 每日快照落盘，长期可回溯；来源网站 / 热门路径保留近 14 天滚动快照
- **我的 GitHub**：OAuth 或 Personal Access Token 登录，浏览自己的仓库与仓库详情，登录后自动触发一次同步
- **发现项目**：免登录搜索、浏览任意 GitHub 公开仓库
- **报表导出**：`daily` / `repos` / `referrers` / `paths` 四类报表，`CSV` / `JSON` / `HTML` 三种格式，可保存到 NAS 共享目录
- **8 套主题**：4 浅 4 深，右上角调色板即时切换，管理员可指定默认主题

## 📦 安装

在 FnDepot 客户端添加本应用源 `https://github.com/MisiteQ/FnDepot` 后，搜索「GStats」一键安装即可；安装后从桌面以窗口化方式打开，或访问 `http://<NAS_IP>/app/gstats/`。

- 对外服务通过 fnOS 统一网关的 **Unix Socket** 提供，无端口冲突
- 以 package 身份（`gstats` 用户）运行，最低 fnOS 版本 **1.1.3100**，依赖应用中心 Node.js v22
- 安装向导需填写 GitHub OAuth App 凭据（也可安装后改用 PAT 登录）

> 统计口径为「访问你 GitHub 仓库的外部访客」，**不记录任何 NAS 用户在应用内的浏览行为**。Traffic API 只对调用者拥有 push 权限的仓库返回数据，无权限仓库自动跳过。

## 🔒 隐私

流量快照保存在应用 var 目录（`TRIM_PKGVAR`）的 `traffic.json`，升级保留；GitHub OAuth token 使用机器绑定密钥 AES 加密后落盘，仅用于读取 GitHub API 与 Traffic 数据。

## 🔗 相关链接

- 项目主页 / 源码：https://github.com/MisiteQ/GStats
- 问题反馈：https://github.com/MisiteQ/GStats/issues
