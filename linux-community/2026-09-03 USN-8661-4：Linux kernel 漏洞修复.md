# Linux 社区动态 | 2026.09.03

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · 通告 5 · 工具链 2

## 🐧 内核版本动态

当前主线 [v7.3-rc1](https://github.com/torvalds/linux/tree/v7.3-rc1)，今日无新版本。

## 🛡 安全通告

### 1. USN-8661-4：Linux kernel 漏洞修复
WiFi mesh 网络对聚合帧处理不当，系 CVE-2020-24588 修复不完整所致（CVE-2025-27558），物理邻近攻击者可注入数据包。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8661-4)*
📅 2026-09-03

### 2. USN-8715-1：Linux kernel (Oracle) 漏洞修复
WiFi mesh 网络聚合帧处理不当，源于 CVE-2020-24588 修复不完整（CVE-2025-27558），邻近攻击者可注入数据包。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8715-1)*
📅 2026-09-03

### 3. USN-8714-1：Linux kernel 漏洞修复
修复多个内核安全问题，涉及 OCFS2 文件系统与 SCTP 协议子系统，攻击者可能利用其入侵系统。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8714-1)*
📅 2026-09-03

### 4. USN-8713-1：BioSig 漏洞修复
BioSig 未正确处理特制输入文件，攻击者可造成拒绝服务或执行任意代码（CVE-2026-22891、CVE-2026-20777）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8713-1)*
📅 2026-09-02

### 5. DSA-6480-1：keystone 安全更新
修复 Debian trixie 中 keystone 的 3 个漏洞（CVE-2026-80182、CVE-2026-80183、CVE-2026-80184），升级至 2:27.0.0-3+deb13u5。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00391.html)*

## 🔬 内核社区与关键机制

### 1. 周三发布 8 个稳定内核
Greg Kroah-Hartman 发布 7.2.3、7.1.13、6.18.49、6.12.108、6.6.156、6.1.187、5.15.220 与 5.10.269 共 8 个稳定内核，各含多项全树重要修复。
📍 *来源：[LWN](https://lwn.net/Articles/1092151/)*
📅 2026-09-02

## 💻 Linus 动态

_今日无新提交。_

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠ 仅剩 4 天）。

## 🔧 工具链更新

### 1. curl 8.22.0（2026-09-02）
第 276 次发布：新增 RFC 9421 HTTP Message Signatures（实验性）与 API guards，支持 Apple GSS Framework 与 fast UDP，移除 TLS-SRP，共修复 9 个安全漏洞、公开 10 个新 CVE。
📍 *来源：[curl Releases](https://github.com/curl/curl/releases/tag/curl-8_22_0)*

### 2. Podman v6.1.1（2026-09-02）
安全修复版：修复 CVE-2026-17106，恶意构造的 tar 归档可利用符号链接将文件写出解压目录之外（Path Traversal）。
📍 *来源：[Podman Releases](https://github.com/podman-container-tools/podman/releases/tag/v6.1.1)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
