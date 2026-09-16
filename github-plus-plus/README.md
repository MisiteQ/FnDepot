# GitHub++ 加速器 (github-plus-plus)

飞牛 fnOS 上的 GitHub / Docker 加速器（FPK 原生应用）：让闲着的 NAS 当局域网加速跳板，家里所有设备直接用，不用每台机器折腾代理和 hosts。

## ✨ 功能

- **Git 加速**：clone / pull 直接走 NAS 中转，不用改 hosts 也不用碰代理软件
- **网页加速**：浏览器直接逛 GitHub，头像、图片正常加载；hosts 模式全局生效无需装证书，进阶可开 MITM 模式（需装一次根证书）
- **Release / raw 下载**：大文件下载稳定不中断
- **Docker 拉取加速**：Docker Hub 拉镜像不再卡在 Waiting，把 registry-mirrors 指向 NAS 即可
- **Web 控制台**：实时测速看哪个源最快、实时日志、在线改配置、侧边栏可折叠、8 套主题切换

原理：内置十多个社区公益加速通道（ghfast.top、gh-proxy.com 等），程序持续测速择优，故障源自动冷却切换；对 API 这类必须直连的域名做了熔断——写客户端前先用 512KB 吞吐探针验证上游真实速度，识别运营商"放行响应头、掐响应体"式 QoS 限速，慢链路自动切镜像，直连恢复后自动切回。

## 📦 安装

在 FnDepot 客户端添加本应用源 `https://github.com/MisiteQ/FnDepot` 后，搜索「GitHub++」一键安装即可；安装后从桌面打开控制台。

- 控制台端口：**7717**；代理端口：**7710**
- 默认账号：**admin / admin123**（登录后请及时修改）
- 应用以 root 身份运行（hosts 加速需写 /etc/hosts），最低 fnOS 版本 **1.0.0**

## 🚀 使用

把下面的 `192.168.31.205` 换成你 NAS 的 IP：

```bash
# git clone
git clone http://192.168.31.205:7710/https://github.com/git/git.git

# Release 文件
curl -LO "http://192.168.31.205:7710/https://github.com/jqlang/jq/releases/download/jq-1.7.1/jq-linux-amd64"

# raw 文件
curl -LO "http://192.168.31.205:7710/https://raw.githubusercontent.com/git/git/master/README.md"
```

Docker 加速：控制台里有说明，把 Docker 的 registry-mirrors 指向 NAS 即可。

## ⚠️ 说明

- 首次登录记得改密码
- MITM 模式的根证书只装在自己的设备上，别外传
- 加速通道为社区公益服务，可用性以实际测速为准

## 🔗 相关链接

- 项目主页 / 源码：https://github.com/MisiteQ/github-plus-plus
- 问题反馈：https://github.com/MisiteQ/github-plus-plus/issues
