# Linux 社区动态 | 2026.09.12

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 2 · 通告 3 · 工具链 1 · Linus 8

## 🐧 内核版本动态

当前主线 [v7.3-rc2](https://github.com/torvalds/linux/tree/v7.3-rc2)，今日无新版本。

## 🛡 安全通告

### 1. USN-8571-2：Apache HTTP Server 修复回归问题
USN-8571-1 的修复因缺少库符号而不完整，引入回归，可能导致 Apache HTTP Server 启动失败
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8571-2)*
📅 2026-09-11

### 2. DSA-6493-1：libevent 安全更新
Debian 更新 libevent，修复多个安全漏洞（涉及 CVE-2026-63379 等 8 个 CVE）
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00404.html)*

### 3. DSA-6492-1：ruby-rack 安全更新
Debian 更新 ruby-rack，修复多个安全漏洞（涉及 CVE-2026-26961 等 13 个 CVE）
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00403.html)*

## 🔬 内核社区与关键机制

### 1. 加速内核构建过程
内核开发者需要频繁构建内核，即便在快机器上也很耗时；内核的构建系统也相当复杂。
📍 *来源：[LWN](https://lwn.net/Articles/1093398/)*
📅 2026-09-11

### 2. 周五发布两个稳定内核更新
Greg Kroah-Hartman 宣布发布 7.2.5 和 6.18.51 稳定内核，各自包含 550 多个补丁，遍布内核树，建议用户升级。
📍 *来源：[LWN](https://lwn.net/Articles/1093766/)*
📅 2026-09-11

## 💻 Linus 动态

### 1. 🔀 合并子系统树 riscv-for-linus-7.3-rc3（09-11）
[查看提交](https://github.com/torvalds/linux/commit/827751b699b79a6e569983359c02dce67f81b94c)

### 2. 🔀 合并子系统树 platform-drivers-x86-v7.3-2（09-11）
[查看提交](https://github.com/torvalds/linux/commit/1235ff329981ecde9ccbf49b83bd4d71e827d541)

### 3. 🔀 合并子系统树 ata-7.3-rc3（09-11）
[查看提交](https://github.com/torvalds/linux/commit/707662b40a82c96e416fe17f3c116a4d648f1fdb)

### 4. 🔀 合并子系统树 block-7.3-20260911（09-11）
[查看提交](https://github.com/torvalds/linux/commit/35ef102063fd6f39e045e6d4e92ac04d3d29c0bf)

### 5. 🔀 合并子系统树 io_uring-7.3-20260911（09-11）
[查看提交](https://github.com/torvalds/linux/commit/42f961c42b6b29532c7c75e028b4192ed333fbcb)

### 6. 🔀 合并子系统树 slab-for-7.3-rc2（09-11）
[查看提交](https://github.com/torvalds/linux/commit/3026c6e4f223bdded6448fefe53ff85d9cbe51bd)

### 7. 🔀 合并子系统树 sound-7.3-rc3（09-11）
[查看提交](https://github.com/torvalds/linux/commit/576da3462c991923ee4aed4bcc22d94531beb0dd)

### 8. 🔀 合并子系统树 media/v7.3-2（09-11）
[查看提交](https://github.com/torvalds/linux/commit/d5d6c9d244c6d447c356df70d5c754b145dccd5c)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.4](https://endoflife.date/openssl) 2026-10-22（⚠ 仅剩 40 天）。

## 🔧 工具链更新

### 1. systemd v259.9（2026-09-11）
systemd-stable 维护版本，仅含相对 v259.8 的小幅回移植修复，详细变更见上游完整 changelog。
📍 *来源：[systemd Releases](https://github.com/systemd/systemd/releases/tag/v259.9)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
