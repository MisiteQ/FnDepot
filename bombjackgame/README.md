# 炸弹杰克（Mighty Bomb Jack）

经典 FC/NES 游戏 **《Mighty Bomb Jack》**（Tecmo/Tehkan，1986/1987）的完全离线版本，安装后出现在飞牛 fnOS 桌面，点击图标即在桌面窗口内直接游玩。**无端口、无后台进程**，基于 WebAssembly 模拟核心，x86 与 ARM 设备通用。

> **发布者声明**：本应用由 [Misite齊（MisiteQ）](https://github.com/MisiteQ) 整理发布，发布者并非游戏的开发者或版权方。游戏名称、角色、画面、音乐及 ROM 版权归原权利方所有，本应用仅为非商业的怀旧保存与技术研究性质再分发。

## ✨ 功能

- **完全离线**：纯 WebAssembly 在浏览器内运行，不联网、不监听端口、无后台服务
- **6 槽位磁盘存档**：存入 / 覆盖 / 读取 / 删除，显示保存时间与大小，数据保存在应用 var 目录（`/var/apps/bombjackgame/var/saves/`），刷新、重启、升级均不丢失，卸载应用也保留
- **自定义按键**：上 / 下 / 左 / 右 / A 跳跃 / B / Start / Select 共 8 个动作均可改键，设置自动保存
- 暂停 / 继续、音量实时调节、4:3 全屏、截图（PNG）、重置回标题画面
- 退出时自动把进度存入空槽位（无空槽则覆盖最早存档）

## 🎮 操作

| 按键 | 功能 |
|---|---|
| 方向键 | 移动 / 上下 |
| X | 跳跃（A，空中按住可悬停） |
| Z | B 键 |
| Enter | 开始 / 暂停 |
| Backspace | Select |
| F8 | 快捷截图 |
| F10 | 重置游戏（回到标题画面） |

## 📦 安装

在 FnDepot 客户端添加本应用源 `https://github.com/MisiteQ/FnDepot` 后，搜索「炸弹杰克」一键安装即可；安装后从桌面点击图标打开。

- 无端口、无后台进程，纯静态 CGI 应用
- 以 package 身份运行，最低 fnOS 版本 **0.9.0**
- 纯 WebAssembly 无原生二进制，x86 / ARM 同一套核心

## 🔧 实现说明

- 模拟核心为 FCEUmm（libretro NES 核心）经 Emscripten 编译的 WebAssembly
- 唯一入口是 `index.cgi`，由 fnOS Web 服务经 `/cgi/ThirdParty/bombjackgame/index.cgi/` 调用，调用前自动校验 NAS 登录态
- 存档 API 与静态资源由 CGI 路由，含目录穿越拦截

## 🔗 相关链接

- 项目主页 / 源码（含 Windows PC 便携版）：https://github.com/MisiteQ/mighty-bomb-jack
- 问题反馈：https://github.com/MisiteQ/mighty-bomb-jack/issues

## ⚠️ 版权

游戏《Mighty Bomb Jack》© Tecmo / Tehkan；模拟核心 FCEUmm © libretro 贡献者（GPLv2）；Emscripten 运行时 © Emscripten 作者（MIT/UIUC）。本应用与 Tecmo、Koei Tecmo、任天堂、飞牛无任何隶属、赞助或认可关系。如权利方认为内容侵权，可通过 Issue 联系发布者处理。
