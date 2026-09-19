# Window Composer

飞牛 fnOS 窗口合成容器应用：把运行在 NAS 上的应用（飞牛应用 / Docker 容器）以**窗口形式编排并输出到 NAS 的物理显示器**。基于 Xorg + openbox + PipeWire + FastAPI，支持 HDMI / DisplayPort / USB-C(DP Alt Mode) / VGA / DVI 等全部显示接口，热插拔自动识别，通过浏览器远程控制面板画框布局、边缘吸附、多窗口不重叠、旋转与截图。

## ✨ 功能

- **🖥️ 通用多接口显示输出**：HDMI / DP / USB-C / VGA / DVI / eDP 全部由同一套 xrandr 解析逻辑覆盖，不写死输出名；多显卡自动选择有显示器接入的 DRM 卡
- **🔌 显示器热插拔守护**：开机没接显示器、之后插上也能自动点亮，换接口/换机器同样自动恢复，无需重启容器
- **🪟 窗口布局管理**：网页可视化拖拽画布，区域拖动/缩放/边缘吸附/防重叠；双击应用卡片一键全屏；多套布局方案 profiles 随时切换
- **📦 应用自动扫描**：自动扫描飞牛 NAS 已安装应用（manifest）与宿主 Docker 容器，一键把应用 Web 界面显示到显示器
- **🔊 音频管理**：读取 PipeWire 音频输出设备列表，每个设备独立音量滑块与静音开关；切换默认设备时正在播放的应用立即迁移
- **📸 屏幕截图**：手动截图 + 定时自动截图（间隔可设，自动只保留最新 200 张）
- **🔄 布局持久化**：保存当前窗口布局，容器重启自动恢复；运行中应用布局不重启、不打断正在播放的视频
- **🔒 访问安全**：访问令牌保护、飞牛 iframe 入口免令牌、跨站请求防护

## 📦 安装

在 FnDepot 客户端中添加本应用源后，搜索「Window Composer」安装即可。安装包很小（不含镜像），安装时会自动对多个 ghcr 加速源测速、择优下载与本机架构匹配的镜像（约 450 MB，仅一次）。安装后桌面打开 **Window Composer**，或直接访问 `http://<NAS_IP>:8181`。

> 安装过程需要 NAS 可访问互联网；完全离线环境可在有 docker 的机器上执行
> `bash scripts/build-package.sh --offline` 自行构建镜像内置的 `-offline.fpk` 安装包。
>
> 应用以 root + privileged 运行：Xorg 的 modesetting 驱动需通过内核 KMS/DRM 打开 DRM master 才能把画面送到物理显示器。

## 🔗 相关链接

- 项目主页 / 源码：https://github.com/MisiteQ/window-composer
- 问题反馈：https://github.com/MisiteQ/window-composer/issues
- 全部版本下载：https://github.com/MisiteQ/window-composer/releases
