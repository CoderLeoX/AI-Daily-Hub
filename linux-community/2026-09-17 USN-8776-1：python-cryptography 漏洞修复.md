# Linux 社区动态 | 2026.09.17

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · 通告 6 · 工具链 2 · Linus 2

## 🐧 内核版本动态

当前主线 [v7.3-rc3](https://github.com/torvalds/linux/tree/v7.3-rc3)，今日无新版本。

## 🛡 安全通告

### 1. USN-8776-1：python-cryptography 漏洞修复
python-cryptography 在执行特定加密操作时错误接受不可变缓冲区对象，导致输出损坏、与预期不符
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8776-1)*
📅 2026-09-17

### 2. USN-8774-1：libheif 漏洞修复
Ali Firas 发现 libheif 对特定图像处理不当，攻击者或可利用该问题造成拒绝服务或执行任意代码（CVE-2026-62291）
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8774-1)*
📅 2026-09-17

### 3. USN-8736-2：Perl 漏洞修复
USN-8736-1 已修复 Perl 漏洞，本次更新为 Ubuntu 24.04 LTS 提供对应修复；原始通告称 Perl 处理特定输入不当
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8736-2)*
📅 2026-09-16

### 4. USN-8773-1：GNU Guix 漏洞修复
GNU Guix 在文件元数据最终确定前就将构建输出暴露给本地用户，本地攻击者或可借此提升权限
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8773-1)*
📅 2026-09-16

### 5. DSA-6496-2 nginx 回归更新
nginx 发布回归更新，修复此前安全更新引入的回归问题（trixie 已修复）
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00411.html)*

### 6. DSA-6499-1 cjose 安全更新
cjose 库安全更新，修复 CVE-2026-53938、CVE-2026-53939 两个漏洞
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00410.html)*

## 🔬 内核社区与关键机制

### 1. Fedora 45 beta 让 Linux 控制台迈入 21 世纪 (Register)
The Register 展望即将发布的 Fedora 45，最大意外是 Linux 传统内核控制台——通常隐藏在图形界面之下的文本模式界面——已被替换
📍 *来源：[LWN](https://lwn.net/Articles/1094762/)*
📅 2026-09-17

## 💻 Linus 动态

### 1. 🔀 合并子系统树 powerpc-7.3-4（09-16）
[查看提交](https://github.com/torvalds/linux/commit/238650ef6c7c7cca08e032527329424c9fbd70e5)

### 2. 🔀 合并子系统树 for-linus（09-14）
[查看提交](https://github.com/torvalds/linux/commit/01414b70cb6f7a5911b65de0cc97225061f60a59)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.4](https://endoflife.date/openssl) 2026-10-22（⚠ 仅剩 35 天）。

## 🔧 工具链更新

### 1. containerd v2.4.0（2026-09-16）
常规版(非 LTS)发布，支持周期较短，面向希望尽早采用新特性的用户。
📍 *来源：[containerd Releases](https://github.com/containerd/containerd/releases/tag/v2.4.0)*

### 2. Podman v5.8.7（2026-09-16）
安全更新：修复 CVE-2025-11395，导入含特制图层的镜像存在风险。
📍 *来源：[Podman Releases](https://github.com/podman-container-tools/podman/releases/tag/v5.8.7)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
