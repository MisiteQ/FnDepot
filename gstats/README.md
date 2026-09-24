# GStats

飞牛 fnOS 上的 GitHub 使用统计平台（FPK 原生应用）：登录自己的 GitHub 账号浏览仓库 / 主页 / Issue，系统自动统计每日登录人数、浏览了哪些项目以及停留时长，并支持导出报表。所有数据仅保存在 NAS 本机，不上传第三方服务器。

## ✨ 功能

- **GitHub 浏览**：OAuth 或 Personal Access Token 登录，浏览自己的仓库、Star 列表、仓库详情、Issues 与 README
- **使用统计**：每日登录人数、活跃人数、登录次数、浏览次数、涉及项目数与停留时长，近 30 天趋势（SVG 折线）与热门项目 Top 榜
- **明细追踪**：每个用户分别查看了什么项目（仓库 / 主页 / Issue / PR），每个项目被谁看了多久（精确到会话级停留时长）
- **报表导出**：`daily` / `users` / `projects` 三类报表，`CSV` / `JSON` / `HTML` 三种格式，可保存到 NAS 共享目录
- **8 套主题**：4 浅 4 深，右上角调色板即时切换，管理员可指定默认主题
- **网络受限适配**：`api.github.com` 不可达时 15 秒内给出错误卡片与重试，管理员可配置 GitHub API 镜像 / 反代地址

## 📦 安装

在 FnDepot 客户端添加本应用源 `https://github.com/MisiteQ/FnDepot` 后，搜索「GStats」一键安装即可；安装后从桌面以窗口化方式打开，或访问 `http://<NAS_IP>/app/gstats/`。

- 对外服务通过 fnOS 统一网关的 **Unix Socket** 提供，无端口冲突
- 以 package 身份（`gstats` 用户）运行，最低 fnOS 版本 **1.1.3100**，依赖应用中心 Node.js v22
- 安装向导需填写 GitHub OAuth App 凭据（也可安装后改用 PAT 登录）

## 🔒 隐私

明细数据（NDJSON）与汇总（JSON）保存在应用 var 目录（`TRIM_PKGVAR`），升级保留；GitHub OAuth token 使用机器绑定密钥 AES 加密后落盘，仅用于读取 GitHub API。

## 🔗 相关链接

- 项目主页 / 源码：https://github.com/MisiteQ/GStats
- 问题反馈：https://github.com/MisiteQ/GStats/issues
