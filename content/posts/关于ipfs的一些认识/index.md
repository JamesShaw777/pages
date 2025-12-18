---
title: 关于ipfs的一些认识
date: 2025-12-18T19:32:17+08:00
lastmod: 2025-12-18T19:32:17+08:00
author: EuanZ
# avatar: /img/author.jpg
# authorlink: https://author.site
cover: cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - 技术
tags:
  - ipfs
  - web3
# nolastmod: true
---

IPFS是一个利用区块链技术实现分布式文件架构的一个协议。

<!--more-->

# IPFS 相关笔记

## ipfs的一些基础知识
IPFS是一个利用区块链技术实现分布式文件架构的一个协议。如果我们允许一个ipfs节点，之后通过此节点上传文件到ipfs网络中，如果其他人对我们的文件进行了同步，那么，此文件按理说就可以永远存在于互联网上。🤔听起来有些像BT，但是加上了区块链的技术，就完全是另一个东西了。

CID 这个可以理解为存储在ipfs网络文件的唯一编码，有了CID，那么就可以通过ipfs网络获取到这个文件。

IPFS网关 这个有点像http打通ipfs网络的一个中间件，通过ipfs网关，就算我们没有安装ipfs相关的软件，也可以通过此网关下载到ipfs网络上的东西

## 有关ipfs的项目

- https://github.com/zu1k/bs-core 一个搜索电子书的项目，也可以通过 https://zlib.missuo.me/ 直接上去体验。
- 搜索完成后下载的时候，会检索所有公开的ipfs网关尝试下载此文件。

## 实际体验？

实际体验上，ipfs给我的感觉依旧不太好，某些时候，即使文件存在于ipfs网络上，但是也取不下来，多次换ipfs网关也取不到文件，估计是网关节点相关文件已经挂掉了。

## 基于ipfs的一些设想

我感觉可以把它当oss来使用，但是响应实在太慢了，而且还有文件丢失的风险，因此，生产环境下还是需要准备一个自己的IPFS节点用于储存。毕竟，所有的东西都是有成本的，白嫖其余的存储节点还是不太现实。