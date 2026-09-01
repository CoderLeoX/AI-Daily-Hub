# Linux 社区动态 | 2026.08.14

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：通告 6 · 工具链 1 · Linus 4

## 🐧 内核版本动态

当前主线 [v7.2-rc7](https://github.com/torvalds/linux/tree/v7.2-rc7)，今日无新版本。

## 🛡️ 安全通告

### 1. USN-8631-3：Linux 内核（NVIDIA Tegra IGX）漏洞
研究人员发现 Linux 内核 WiFi 实现因 CVE 修复不当，未能正确处理网状网络中的聚合帧。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8631-3)*
📅 2026-08-14

### 2. USN-8633-2：Linux 内核漏洞
研究人员发现 Linux 内核 WiFi 实现因 CVE 修复不当，未能正确处理网状网络中的聚合帧。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8633-2)*
📅 2026-08-14

### 3. USN-8529-2：Linux 内核漏洞
研究发现 Linux 内核 XFRM ESP-in-TCP 子系统处理 socket buffer 片段时存在逻辑缺陷（Fragnesia），本地攻击者可利用该漏洞。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8529-2)*
📅 2026-08-14

### 4. USN-8548-2：Linux 内核漏洞
研究发现 Linux 内核 XFRM ESP-in-TCP 子系统处理 socket buffer 片段时存在逻辑缺陷（Fragnesia），本地攻击者可利用该漏洞。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8548-2)*
📅 2026-08-14

### 5. DSA-6437-1：apr-util 安全更新
Debian 安全通告，具体内容详见来源链接。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00348.html)*

### 6. DSA-6436-1：Chromium 安全更新
Debian 安全通告，具体内容详见来源链接。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00347.html)*

## 🔬 内核社区与关键机制

_今日无新增文章。_

## 💻 Linus 动态

### 1. 🔀 合并子系统树 net-7.2-rc8（08-13）
[查看提交](https://github.com/torvalds/linux/commit/e14aacefb78d942d2308d9821fe52d75d21a824e)

### 2. 🔀 合并子系统树 firewire-fixes-7.2-final（08-13）
[查看提交](https://github.com/torvalds/linux/commit/83a4f90e9835d3d61fe3dd39ffbbcac752467d09)

### 3. 🔀 合并子系统树 gpio-fixes-for-v7.2（08-13）
[查看提交](https://github.com/torvalds/linux/commit/b4f5144d37403d529334573ef2a1bb6ca4a2c553)

### 4. 🔀 合并子系统树 m68k-for-v7.2-tag2（08-13）
[查看提交](https://github.com/torvalds/linux/commit/64dc3ba55effbf8afcc0099162dfb4138009ad48)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.0 LTS](https://endoflife.date/openssl) 2026-09-07（⚠️ 仅剩 24 天）。

## 🔧 工具链更新

### 1. Podman v5.8.6（2026-08-13）
### Security - This release addressed [CVE-2026-19730](https://github.com/podman-container-tools/podman/security/advisories/GHSA-fx76-2j3w-2mx6) where the `podman quadlet install --replace` command did not truncate the file being replaced, meaning replacing a longer file with a shorter one would res
📍 *来源：[Podman Releases](https://github.com/podman-container-tools/podman/releases/tag/v5.8.6)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
