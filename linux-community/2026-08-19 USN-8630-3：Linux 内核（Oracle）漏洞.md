# Linux 社区动态 | 2026.08.19

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · 通告 6 · Linus 8

## 🐧 内核版本动态

当前主线 [v7.2](https://github.com/torvalds/linux/tree/v7.2)，今日无新版本。

## 🛡 安全通告

### 1. USN-8630-3：Linux 内核（Oracle）漏洞
Linux 内核发现多个安全问题，攻击者可能借此入侵系统；本次更新修复 x86 架构子系统的缺陷。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8630-3)*
📅 2026-08-19

### 2. USN-8636-2：Linux 内核（Oracle）漏洞
Linux 内核发现多个安全问题，攻击者可能借此入侵系统；本次更新修复 x86 架构子系统的缺陷。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8636-2)*
📅 2026-08-19

### 3. USN-8629-3：Linux 内核（HWE）漏洞
Linux 内核发现多个安全问题，攻击者可能借此入侵系统；本次更新修复 x86 架构子系统的缺陷。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8629-3)*
📅 2026-08-19

### 4. USN-8646-1：Linux 内核漏洞
Linux 内核发现多个安全问题，攻击者可能借此入侵系统；本次更新修复 OCFS2 文件系统子系统的缺陷。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8646-1)*
📅 2026-08-19

### 5. DSA-6448-1：spip 安全更新
Debian 发布 spip 安全更新，建议及时升级修复。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00359.html)*

### 6. DSA-6447-1：librabbitmq 安全更新
Debian 发布 librabbitmq 安全更新，建议及时升级修复。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00358.html)*

## 🔬 内核社区与关键机制

### 1. Fedora 准备终结 AF_ALG
内核 Crypto API 的用户空间接口 AF_ALG 与近期多起重大安全漏洞相关，包括 Copy Fail 及其后续变种漏洞。
📍 *来源：[LWN](https://lwn.net/Articles/1088489/)*
📅 2026-08-18

## 💻 Linus 动态

### 1. 🔀 合并子系统树 x86-documentation-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/3a0dd7ba4f44cdc116d83712f61e7c1a95be3588)

### 2. 🔀 合并子系统树 x86-core-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/d5b550edadab6810653f287715a0d696306b6ae0)

### 3. 🔀 合并子系统树 x86-build-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/3dd1f7447f4f989b3a348cdc347b15397d03bebc)

### 4. 🔀 合并子系统树 x86-boot-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/09d639f1f1f6347eb28802799a2187ae540b00ba)

### 5. 🔀 合并子系统树 x86-msr-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/8dcef8882aad8f1b8668d1c39968cde99312aa3c)

### 6. 🔀 合并子系统树 sched-core-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/e2457a664ea02c414c6b9828bff3a0df4c300f63)

### 7. 🔀 合并子系统树 locking-core-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/dfa35434d7f20142fedd7120277b1044a0a2bb64)

### 8. 🔀 合并子系统树 perf-core-2026-08-17（08-18）
[查看提交](https://github.com/torvalds/linux/commit/8915457146a11d20a6c0786396376afda65eec40)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠ 仅剩 19 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
