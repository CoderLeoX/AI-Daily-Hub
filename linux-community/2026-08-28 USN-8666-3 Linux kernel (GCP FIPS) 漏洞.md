# Linux 社区动态 | 2026.08.28

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · 通告 6 · Linus 8

## 🐧 内核版本动态

当前主线 [v7.2](https://github.com/torvalds/linux/tree/v7.2)，今日无新版本。

## 🛡️ 安全通告

### 1. USN-8666-3: Linux kernel (GCP FIPS) 漏洞
研究人员发现，Linux kernel 的 WiFi 实现因某 CVE 修复不正确，未能在 mesh 网络中正确处理聚合帧（aggregated frames）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8666-3)*
📅 2026-08-28

### 2. USN-8644-3: Linux kernel (Azure) 漏洞
修复 Linux kernel 多个子系统（含文件系统基础设施等）的安全缺陷，攻击者可能借此危害系统。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8644-3)*
📅 2026-08-28

### 3. USN-8661-3: Linux kernel 漏洞
研究人员发现，Linux kernel 的 WiFi 实现因某 CVE 修复不正确，未能在 mesh 网络中正确处理聚合帧（aggregated frames）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8661-3)*
📅 2026-08-28

### 4. USN-8658-4: Linux kernel (Azure CVM) 漏洞
修复 Linux kernel 多个子系统（含 Open vSwitch 等）的安全缺陷，攻击者可能借此危害系统。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8658-4)*
📅 2026-08-28

### 5. DSA-6476-1 chromium 安全更新
Debian 发布 chromium 安全更新，修复多个安全漏洞，建议尽快升级。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00387.html)*

### 6. DSA-6475-1 suricata-update 安全更新
Debian 发布 suricata-update 安全更新，修复安全漏洞，建议尽快升级。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00386.html)*

## 🔬 内核社区与关键机制

### 1. 周四发布八个稳定内核
Greg Kroah-Hartman 发布 7.2.1、7.1.11、6.18.47、6.12.106、6.6.154、6.1.185、5.15.218、5.10.267 共 8 个稳定版内核，均含重要更新。
📍 *来源：[LWN](https://lwn.net/Articles/1090940/)*
📅 2026-08-27

## 👨‍💻 Linus 动态

### 1. 🔀 合并子系统树 net-7.3-rc1（08-27）
[查看提交](https://github.com/torvalds/linux/commit/1b78070aaef63512688aebfbc82365ef9d6660f1)

### 2. 🔀 合并子系统树 devicetree-fixes-for-7.3-1（08-27）
[查看提交](https://github.com/torvalds/linux/commit/3ba13f5e7180c034b0a1ef7e052fb780856b134e)

### 3. 🔀 合并子系统树 spi-fix-v7.3-merge-window（08-27）
[查看提交](https://github.com/torvalds/linux/commit/9bb34313d94b17a379ea68fae65be0810c88ee64)

### 4. 🔀 合并子系统树 regulator-fix-v7.3-merge-window（08-27）
[查看提交](https://github.com/torvalds/linux/commit/6253a29206959128f5d99a119fcf29bd7fb3c106)

### 5. 🔀 合并子系统树 dma-mapping-7.3-2026-08-27（08-27）
[查看提交](https://github.com/torvalds/linux/commit/7cec13314dd8935afbfc0430d9d43fad75285b37)

### 6. 🔀 合并子系统树 backlight-next-7.3（08-27）
[查看提交](https://github.com/torvalds/linux/commit/f7e3f4d9f425cf4c5577cd84a096e6e618488083)

### 7. 🔀 合并子系统树 leds-next-7.3（08-27）
[查看提交](https://github.com/torvalds/linux/commit/7cc2726d4847c48844eb0ee16f973d449260f248)

### 8. 🔀 合并子系统树 mfd-next-7.3（08-27）
[查看提交](https://github.com/torvalds/linux/commit/79b4f3baae2fa65060c30f827e3c0e8f1db99f98)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠️ 仅剩 10 天）。

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
