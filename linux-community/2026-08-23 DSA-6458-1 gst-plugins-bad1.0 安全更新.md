# Linux 社区动态 | 2026.08.23

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：通告 2 · Linus 4

## 🐧 内核版本动态

当前主线 [v7.2](https://github.com/torvalds/linux/tree/v7.2)，今日无新版本。

## 🛡️ 安全通告

### 1. DSA-6458-1 gst-plugins-bad1.0 安全更新
修复 GStreamer 媒体解析器多处越界读写漏洞，恶意媒体文件可致崩溃、信息泄露甚至任意代码执行
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00369.html)*

### 2. DSA-6457-1 openjdk-21 安全更新
修复 OpenJDK Java 运行时多个漏洞，可能导致拒绝服务或信息泄露
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00368.html)*

## 🔬 内核社区与关键机制

_今日无新增文章。_

## 💻 Linus 动态

### 1. 🔀 合并子系统树 caps-pr-20260820（08-22）
[查看提交](https://github.com/torvalds/linux/commit/66fb95a521110da673090294561844c9f76ebe64)

### 2. 🔀 合并子系统树 exfat-for-7.3-rc1（08-22）
[查看提交](https://github.com/torvalds/linux/commit/728785f8fb07ae9c295b1be6d7d672b9ebfc3c05)

### 3. 🔀 合并子系统树 perf-tools-for-v7.3-2026-08-21（08-22）
[查看提交](https://github.com/torvalds/linux/commit/473f6c8f437b049f8ec015d57cd59bb983b1d85c)

### 4. 🔀 合并子系统树 firewire-updates-7.3（08-22）
[查看提交](https://github.com/torvalds/linux/commit/47f05f71ad988c3180bdba807151e6e86ed75aa3)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠️ 仅剩 15 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
