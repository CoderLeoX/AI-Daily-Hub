# Linux 社区动态 | 2026.09.22

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 3 · 通告 4 · Linus 4

## 🐧 内核版本动态

当前主线 [v7.3-rc4](https://github.com/torvalds/linux/tree/v7.3-rc4)，今日无新版本。

## 🛡 安全通告

### 1. USN-8798-1: GStreamer Good Plugins 漏洞
GStreamer Good Plugins 解析 MRF 文件存在缺陷，远程攻击者可利用该问题执行任意代码（CVE-2026-18295、CVE-2026-18296）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8798-1)*
📅 2026-09-22

### 2. USN-8797-1: GStreamer Base Plugins 漏洞
GStreamer Base Plugins 处理特定 OGG 媒体文件不当，打开特制文件时远程攻击者可能执行任意代码。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8797-1)*
📅 2026-09-22

### 3. USN-8794-1: GLib 漏洞
GLib 的 GDBus 认证机制未限制从客户端读取的数据行长度，未认证攻击者可造成拒绝服务。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8794-1)*
📅 2026-09-22

### 4. USN-8790-1: Expat 漏洞
Expat 解析小型构造文档时可能分配大量内存，攻击者可借此耗尽资源。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8790-1)*
📅 2026-09-21

## 🔬 内核社区与关键机制

### 1. 三个新的 stable 内核发布
Greg Kroah-Hartman 发布 7.2.7、6.18.53 和 6.12.111 稳定内核，照例体量很大，并包含大量重要修复。
📍 *来源：[LWN](https://lwn.net/Articles/1095703/)*
📅 2026-09-21

### 2. 用 Linux Test Project 在 NetBSD 上测试 compat_linux
NetBSD 长期通过内核级 compat_linux 支持运行 Linux 二进制，但测试覆盖不足，此项工作意在补齐。
📍 *来源：[LWN](https://lwn.net/Articles/1094310/)*
📅 2026-09-21

### 3. 内核预补丁 7.3-rc4
Linus Torvalds 发布 7.3-rc4 预补丁，照例体量很大："这套说辞大家都熟了：它很大，如此这般"。
📍 *来源：[LWN](https://lwn.net/Articles/1095491/)*
📅 2026-09-21

## 💻 Linus 动态

### 1. 🔀 合并子系统树 xfs-fixes-7.3-rc5（09-21）
[查看提交](https://github.com/torvalds/linux/commit/f0100363d8c374bd8e9ea7c9ba02744f0b802ca4)

### 2. 🔀 合并子系统树 soundwire-7.3-fixes（09-20）
[查看提交](https://github.com/torvalds/linux/commit/0a885f68d0e90dcef77e575b09104df7263e2aca)

### 3. 🔀 合并子系统树 x86-urgent-2026-09-20（09-20）
[查看提交](https://github.com/torvalds/linux/commit/156fa7417fac89fd9dcf3a4ee88785ff90ab6411)

### 4. 🔀 合并子系统树 timers-urgent-2026-09-20（09-20）
[查看提交](https://github.com/torvalds/linux/commit/0a15ba6b0c3adec5842d4252c3e5d2ca935e9948)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.4](https://endoflife.date/openssl) 2026-10-22（⚠ 仅剩 30 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
