# MisiteQ 的 FnDepot 应用源

本仓库是 [FnDepot](https://github.com/EWEDLCM/FnDepot) 外部应用源（V2 规范），提供飞牛 fnOS 第三方应用的安装索引。在 FnDepot 客户端中添加本仓库地址后，即可搜索并一键安装 / 升级其中的应用。

## 📥 如何添加本应用源

1. 在飞牛 fnOS 上安装并打开 **FnDepot** 客户端
2. 进入「应用源 / 源管理」，选择添加 GitHub 仓库源
3. 填入本仓库地址：
```
https://github.com/MisiteQ/FnDepot
```
4. 保存后即可在应用列表中搜索到本源提供的应用

也可以直接添加 `fnpack.json` 直链： `https://raw.githubusercontent.com/MisiteQ/FnDepot/main/fnpack.json`

## 📦 源内应用

| 应用 | 说明 | 架构 |
|---|---|---|
| [惬意阅读 (QYRead)](https://github.com/MisiteQ/FnDepot/blob/main/qyread/README.md) | 飞牛上的私人书库与阅读中心：多格式书库（TXT/EPUB/MOBI/AZW3/PDF/CBZ/CBR/CB7）、小说聚合搜索下载（可暂停/继续/取消）、沉浸阅读、Edge 听书、批注笔记与阅读统计 | x86 / arm |
| [飞牛监控 (fnMonitor)](https://github.com/MisiteQ/FnDepot/blob/main/fnmonitor/README.md) | fnOS 系统监控面板：实时监控 CPU / 内存 / 磁盘 / 网络 / 温度 / 功耗 / GPU 与 Docker，支持流量统计、功耗统计、历史趋势与数据持久化 | x86 / arm |

## 🗂 仓库结构

```
FnDepot/
├── fnpack.json      # FnDepot V2 应用源索引（根目录，文件名固定）
├── README.md        # 本说明
├── qyread/          # 惬意阅读应用目录
│   ├── ICON.PNG     # 应用图标
│   ├── README.md    # 应用详情说明
│   └── fpk/         # 各架构安装包
│       ├── qyread-0.1.20-x86.fpk
│       └── qyread-0.1.20-arm.fpk
└── fnmonitor/       # 飞牛监控应用目录
    ├── ICON.PNG     # 应用图标
    ├── README.md    # 应用详情说明
    └── fpk/         # 各架构安装包
        ├── fnmonitor-2.12.2-x86.fpk
        └── fnmonitor-2.12.2-arm.fpk
```
`fnpack.json` 中的资源与安装包均使用相对路径定位，随仓库一起分发，无需依赖外部下载地址。

## 🔧 规范

本源遵循 [FnDepot 外部应用源 V2 编写说明](https://github.com/EWEDLCM/FnDepot/blob/main/README.md)：根目录 `fnpack.json` 包含 `schema_version: "2"`、`source_info` 与 `apps`，应用键名与 FPK manifest 的 `appname` 一致。

## ⚠️ 说明

外部源由用户自行添加，仅在用户本地客户端中生效。应用的代码、安装包安全性与运行稳定性由应用开发者负责。
