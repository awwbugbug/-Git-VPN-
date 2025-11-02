# 🛰️ Git 无法连接 GitHub 的解决方案（Clash Verge 环境）

本教程适用于 Windows 系统下使用 **Clash Verge** 代理时，执行  
`git clone` 或 `git fetch` 等命令出现：
```bash
fatal: unable to access 'https://github.com/xxx.git/
':
Failed to connect to github.com port 443 after xxxx ms: Could not connect to server
---
```
# ⚙️ 一、确认 Clash Verge 代理端口

1. 打开 Clash Verge → 查看面板信息  
2. 找到以下字段（示例）：
```bash
内核版本: v1.19.11 Mihomo
系统代理地址: 127.0.0.1:7897
混合代理端口: 7897
```

说明 Clash 正在监听本地端口 `7897`，即 HTTP 与 SOCKS5 混合代理端口。

---

## 🌐 二、配置 Git 全局代理

在 PowerShell 或 CMD 中执行以下命令：

```bash
git config --global http.proxy http://127.0.0.1:7897
git config --global https.proxy http://127.0.0.1:7897
```
检查是否设置成功：
```bash
git config --global --get http.proxy
git config --global --get https.proxy
```
输出应为：
```bash
http://127.0.0.1:7897
```
# 🚀 三、重新尝试 Git 操作
```
git clone https://github.com/***/***.git
```
# 🧩 四、可选配置：取消代理

当你不再使用代理（例如校园网或内网环境）时，可以取消设置：
```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```
# 💡 五、附加提示

若仍然无法连接，请确认：

Clash Verge 中已开启「允许来自局域网的连接」。

Clash Verge 启用了「系统代理」。

你的订阅或代理节点本身可正常访问 GitHub。

