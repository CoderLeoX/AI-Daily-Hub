# Linux 社区动态 | 2026.09.16

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · 通告 4 · 工具链 1 · Linus 5

## 🐧 内核版本动态

当前主线 [v7.3-rc3](https://github.com/torvalds/linux/tree/v7.3-rc3)，今日无新版本。

## 🛡 安全通告

### 1. USN-8770-1: SimpleSAMLphp 漏洞
发现 SimpleSAMLphp 校验 XML 消息中的加密签名不当，已认证攻击者可能借此冒充用户或获取更高权限。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8770-1)*
📅 2026-09-16

### 2. USN-8769-1: phpseclib 漏洞
发现 phpseclib 在 AES CBC 模式下未以恒定时间校验填充，远程攻击者可能发动 padding oracle 计时攻击。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8769-1)*
📅 2026-09-15

### 3. USN-8768-1: Shibboleth 漏洞
Florian Stuhlmann 发现 Shibboleth 的 ODBC 存储插件未正确转义输入，远程攻击者可能实施 SQL 注入并获取敏感信息。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8768-1)*
📅 2026-09-15

### 4. USN-8767-1: Snapcast 漏洞
发现 Snapcast 处理特制 JSON-RPC 请求不当，远程攻击者可能执行任意代码或获取敏感信息。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8767-1)*
📅 2026-09-15

## 🔬 内核社区与关键机制

### 1. 为 blk-iocost 引入 BPF 支持
blk-iocost 面向固态盘设计、性能良好但仍有提升空间；Tao Cui 的补丁系列允许加载 BPF 程序制定成本决策，使其更灵活。
📍 *来源：[LWN](https://lwn.net/Articles/1093661/)*
📅 2026-09-15

## 💻 Linus 动态

### 1. 🔀 合并子系统树 sched_ext-for-7.3-rc3-fixes（09-15）
[查看提交](https://github.com/torvalds/linux/commit/9b87fdc9af2fbfcdb5c24a64139685ef80f6573f)

### 2. 🔀 合并子系统树 cgroup-for-7.3-rc3-fixes（09-15）
[查看提交](https://github.com/torvalds/linux/commit/6fb20c02710dabc2f63aa21cb23a154d76ef9921)

### 3. 🔀 合并子系统树 sysctl-7.03-fixes-rc4（09-15）
[查看提交](https://github.com/torvalds/linux/commit/f6e7b42bf05b2427fb8a7a1d1c387a86638bb413)

### 4. 🔀 合并子系统树 for-linus（09-14）
[查看提交](https://github.com/torvalds/linux/commit/01414b70cb6f7a5911b65de0cc97225061f60a59)

### 5. 🔀 合并子系统树 mm-hotfixes-stable-2026-09-13-21-50（09-14）
[查看提交](https://github.com/torvalds/linux/commit/164f652b6ef9209437ca016beedfcab626ff4f02)

## ⏳ LTS / EOL 生命周期

状态无变化，最近到期：[openssl 3.4](https://endoflife.date/openssl) 2026-10-22（⚠ 仅剩 36 天）。

## 🔧 工具链更新

### 1. Docker Engine 29.8.1 发布：修复镜像加载与网络过滤（2026-09-15）
修复 docker load 残留悬空镜像、OpenVZ 命名空间检测、Windows 提交容器硬链接丢失、type 过滤返回 500；containerd 升级至 v2.3.5。
📍 *来源：[Docker Engine Releases](https://github.com/moby/moby/releases/tag/docker-v29.8.1)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
