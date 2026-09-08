# Linux 社区动态 | 2026.09.09

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：通告 5 · Linus 3

## 🐧 内核版本动态

当前主线 [v7.3-rc2](https://github.com/torvalds/linux/tree/v7.3-rc2)，今日无新版本。

## 🛡 安全通告

### 1. USN-8737-1：GNU C Library 漏洞
strfmon 右对齐填充存在缓冲区溢出、tdelete 越界栈访问、wordexp 内存处理错误等多项缺陷，攻击者可利用导致拒绝服务或任意代码执行。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8737-1)*
📅 2026-09-08

### 2. USN-8736-1：Perl 漏洞
Perl 处理正则匹配的特定大输入及含交替分支的正则时出错，可致越界堆读写（拒绝服务或任意代码执行），或导致正则匹配错误、安全限制被绕过。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8736-1)*
📅 2026-09-08

### 3. USN-8735-1：HSQLDB 漏洞
HSQLDB 错误处理特制的数据库文件，攻击者可利用该问题覆盖任意文件。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8735-1)*
📅 2026-09-08

### 4. USN-8734-1：PHP 漏洞
配置 typemap 的 SOAP 服务器做 Apache map 解码时触发空指针解引用、metaphone() 有符号整数溢出致越界读、phar 归档循环符号链接致无限递归，可造成拒绝服务。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8734-1)*
📅 2026-09-07

### 5. DSA-6489-1：gst-plugins-base1.0 安全更新
GStreamer 基础插件库修复 CVE-2026-18297，Debian trixie 已更新至 1.26.2-1+deb13u2。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00400.html)*

## 🔬 内核社区与关键机制

_今日无新增文章。_

## 💻 Linus 动态

### 1. 🔀 合并子系统树 x86_urgent_for_7.3-rc3（09-08）
[查看提交](https://github.com/torvalds/linux/commit/893e11787f78e43b534e252249ac3fff4d1333f8)

### 2. 🔀 合并子系统树 powerpc-7.3-2（09-08）
[查看提交](https://github.com/torvalds/linux/commit/5acbae5f7eb3d5275120abfe698c394b7325dcec)

### 3. 🔀 合并子系统树 v7.3-p3（09-08）
[查看提交](https://github.com/torvalds/linux/commit/7daadf5131ed488037cc4540797e53c7f2c5d3ec)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.4](https://endoflife.date/openssl) 2026-10-22（⚠ 仅剩 43 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
