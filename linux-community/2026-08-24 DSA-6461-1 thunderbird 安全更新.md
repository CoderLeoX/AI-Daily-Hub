# Linux 社区动态 | 2026.08.24

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 2 · 通告 2 · Linus 8

## 🐧 内核版本动态

当前主线 [v7.2](https://github.com/torvalds/linux/tree/v7.2)，今日无新版本。

## 🛡 安全通告

### 1. DSA-6461-1 thunderbird 安全更新
修复 13 个 CVE（CVE-2026-74963 至 CVE-2026-74990 等），trixie 修复版 1:140.14.0esr-1~deb13u1
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00372.html)*

### 2. DSA-6460-1 openjdk-25 安全更新
修复 4 个 CVE（CVE-2026-60589、CVE-2026-61308、CVE-2026-70906、CVE-2026-70907），trixie 修复版 25.0.4.1+1-1~deb13u1
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00371.html)*

## 🔬 内核社区与关键机制

### 1. 周日发布新一批稳定内核
7.1.10、6.18.46、6.12.105、6.6.153、6.1.184、5.15.217、5.10.266 七个稳定内核均已发布，各含一批重要修复。
📍 *来源：[LWN](https://lwn.net/Articles/1090099/)*
📅 2026-08-23

### 2. 悼念 Steve French
Jeremy Allison 带来噩耗：Steve French 辞世，他曾多年担任内核 SMB 文件系统代码维护者，后因健康问题卸任。
📍 *来源：[LWN](https://lwn.net/Articles/1090098/)*
📅 2026-08-23

## 💻 Linus 动态

### 1. 🔀 合并子系统树 i3c/for-7.3（08-23）
[查看提交](https://github.com/torvalds/linux/commit/4352b8aee98005853aa63f57d6377282de17a33f)

### 2. 🔀 合并子系统树 pci-v7.3-changes（08-23）
[查看提交](https://github.com/torvalds/linux/commit/570f7e331f5febb30f1384817463c7e42b65ca7d)

### 3. 🔀 合并子系统树 parisc-for-7.3-rc1（08-23）
[查看提交](https://github.com/torvalds/linux/commit/b6b019a1d9b90ac51174f0ca15b1338b61506bf9)

### 4. 🔀 合并子系统树 s390-7.3-1（08-23）
[查看提交](https://github.com/torvalds/linux/commit/66ec24c5d7a047f5b06ee1deb1d0a2869b1791bd)

### 5. 🔀 合并子系统树 efi-next-for-v7.3（08-23）
[查看提交](https://github.com/torvalds/linux/commit/388b607d107c07aaade04c7f22f344cab6bdccd3)

### 6. 🔀 合并子系统树 liveupdate-v7.3-rc1-20260823（08-23）
[查看提交](https://github.com/torvalds/linux/commit/91959a31a3990073b55b506af044eda09c359fb4)

### 7. 🔀 合并子系统树 mtd/for-7.3（08-23）
[查看提交](https://github.com/torvalds/linux/commit/df51bdc5e80dae43cab81f6cc641e98638303c88)

### 8. 🔀 合并子系统树 ksmbd-for-7.3-rc1（08-23）
[查看提交](https://github.com/torvalds/linux/commit/61a09cfc121472013f99ae75066676739a5db626)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠ 仅剩 14 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
