---
title: NordVPN 提取 WireGuard 配置文件
date: 2025-11-29T20:38:07+08:00
lastmod: 2025-11-29T20:38:07+08:00
author: EuanZ
# avatar: /img/author.jpg
# authorlink: https://author.site
cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - 技术
tags:
  - 上网
draft: false

nolastmod: false
---

NordVPN 宣传自己基于 WireGuard 自研了 NordLynx 协议，但实际上此协议与原生 WireGuard 完全兼容，可以完美运行在任何 WireGuard 客户端上，换句话说，**这就是 WireGuard 协议**。

 
 <!--more-->>
# NordVPN 提取 WireGuard 配置文件（NordLynx 其实就是 WireGuard）

NordVPN 宣传自己基于 WireGuard 自研了 NordLynx 协议，但实际上此协议与原生 WireGuard 完全兼容，可以完美运行在任何 WireGuard 客户端上，换句话说，**这就是 WireGuard 协议**。

## 提取完整配置文件（推荐）

### 利用 Docker 一键生成所有服务器配置文件
参考 GitHub 项目：  
https://github.com/mustafachyi/NordVPN-WireGuard-Config-Generator

> 需要提前在 NordVPN 仪表盘中获取 token（有效期通常 30 天）

```bash
docker run -it --rm -v "$(pwd)/generated_configs:/data" mustafachyi/nordgen:latest
```

运行后提示输入 token，粘贴即可。
程序会自动生成所有国家/城市的 .conf 文件，保存在当前目录的 generated_configs 文件夹中。

### 单独获取自己的 WireGuard PrivateKey
因为所有 NordVPN WireGuard 服务器的公钥都是固定的，只要把私钥换成你自己的，任何配置文件都能正常使用。
操作步骤：

先获取 token（同上）
安装 jq（Linux/macOS 直接安装，Windows 建议用 WSL 或 Git Bash）

> 📌 **注意：把 <ACCESS_TOKEN> 替换成你自己的 token**
```bash
curl -s -u token:<ACCESS_TOKEN> https://api.nordvpn.com/v1/users/services/credentials | jq -r .nordlynx_private_key
```

执行完毕，即可获取到自己账户的 PrivateKey