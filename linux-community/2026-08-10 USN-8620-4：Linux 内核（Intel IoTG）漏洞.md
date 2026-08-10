# Linux 社区动态 | 2026.08.10

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。

## 🐧 内核版本动态

| 版本 | 阶段 |
| --- | --- |
| [v7.2-rc7](https://github.com/torvalds/linux/tree/v7.2-rc7) | Linux 7.2 第 7 个发布候选版 (RC) |
| [v7.2-rc6](https://github.com/torvalds/linux/tree/v7.2-rc6) | Linux 7.2 第 6 个发布候选版 (RC) |
| [v7.2-rc5](https://github.com/torvalds/linux/tree/v7.2-rc5) | Linux 7.2 第 5 个发布候选版 (RC) |
| [v7.2-rc4](https://github.com/torvalds/linux/tree/v7.2-rc4) | Linux 7.2 第 4 个发布候选版 (RC) |
| [v7.2-rc3](https://github.com/torvalds/linux/tree/v7.2-rc3) | Linux 7.2 第 3 个发布候选版 (RC) |
| [v7.2-rc2](https://github.com/torvalds/linux/tree/v7.2-rc2) | Linux 7.2 第 2 个发布候选版 (RC) |
| [v7.2-rc1](https://github.com/torvalds/linux/tree/v7.2-rc1) | Linux 7.2 第 1 个发布候选版 (RC) |
| [v7.1](https://github.com/torvalds/linux/tree/v7.1) | Linux 7.1 正式版 |

## 🛡️ 安全通告

### 1. USN-8620-4：Linux 内核（Intel IoTG）漏洞
Maxim Suhanov 发现 Linux 内核 NTFS 文件系统实现对文件名长度校验不严，特定情况下导致越界读取（out-of-bounds read），攻击者可……（原文截断）
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8620-4)*
📅 2026-07-31

### 2. USN-8620-3：Linux 内核（Intel IoTG）漏洞
同 USN-8620-4，Maxim Suhanov 发现 NTFS 文件名长度校验缺陷导致越界读取，攻击者可……（原文截断）
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8620-3)*
📅 2026-07-31

### 3. USN-8625-1：OpenSSL 漏洞
发现 OpenSSL 在接收握手数据时于 SSL/TLS 状态机中错误分配内存缓冲区，远程攻击者可能利用此问题导致 OpenSSL 消耗……（原文截断）
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8625-1)*
📅 2026-07-30

### 4. USN-8624-1：Sinatra 漏洞
发现 Sinatra 未正确处理 header 解析，特定输入会使 ETag 生成挂起，远程攻击者可能利用此问题造成拒绝服务
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8624-1)*
📅 2026-07-30

### 5. DSA-6424-1：Xen 安全更新
无摘要内容（原文仅提供通告链接）
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00335.html)*

### 6. DSA-6423-1：kitty 安全更新
无摘要内容（原文仅提供通告链接）
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00334.html)*

## 🔬 内核社区与关键机制

### 1. 内核预备版 7.2-rc7 发布
7.2-rc7 预备版内核发布供测试，虽仍偏大，但 Linus 表示目前看不到推迟 7.2 正式版发布的必要，预计如期发布。
📍 *来源：[LWN](https://lwn.net/Articles/1087961/)*
📅 2026-08-10

### 2. 四个周末稳定版内核更新
7.1.8、6.18.44、6.12.103 和 6.6.151 稳定版内核发布，各自包含相当数量的重要修复。
📍 *来源：[LWN](https://lwn.net/Articles/1087949/)*
📅 2026-08-10

### 3. 周五稳定版内核：单一 bug 修复
Greg Kroah-Hartman 宣布发布 6.12.102、6.6.150、6.1.182、5.15.215、5.10.264 稳定版内核，本轮仅包含对单一 bug 的修复。
📍 *来源：[LWN](https://lwn.net/Articles/1087743/)*
📅 2026-08-07

### 4. 六个稳定版内核含安全修复
Greg Kroah-Hartman 宣布发布 7.1.7、6.18.43、6.6.149、6.1.181、5.15.214、5.10.263 稳定版内核，修复安全漏洞 CVE-2026-68480。
📍 *来源：[LWN](https://lwn.net/Articles/1087567/)*
📅 2026-08-07

### 5. 将 BPF 引入 binfmt_misc
内核能运行 ELF 原生二进制、#! 开头的解释型脚本等多种可执行文件，此外还具备一种名为 binfmt_misc 的机制。
📍 *来源：[LWN](https://lwn.net/Articles/1086947/)*
📅 2026-08-06

### 6. b4 0.16.0 发布
Konstantin Ryabitsev 宣布发布软件开发工具 b4 0.16.0，最大变化是新增 bug 跟踪支持：新命令 "b4 bugs" 集成该功能。
📍 *来源：[LWN](https://lwn.net/Articles/1087388/)*
📅 2026-08-06

### 7. 用 BPF 检查其他网络命名空间
Jordan Rife 为 Cilium 编写与 Kubernetes 网络交互的 BPF 程序，希望让具备适当权限的 BPF 程序能遍历其他网络命名空间。
📍 *来源：[LWN](https://lwn.net/Articles/1085896/)*
📅 2026-08-06

### 8. FUSE 状态与计划
FUSE 维护者 Miklos Szeredi 在 2026 Linux Storage、Filesystem、Memory Management 和 BPF Summit 上主持了该子系统的 BoF 讨论。
📍 *来源：[LWN](https://lwn.net/Articles/1086336/)*
📅 2026-08-05

## 👨‍💻 Linus 动态

### 1. 🏷️ 版本发布 Linux 7.2-rc7（08-09）
[查看提交](https://github.com/torvalds/linux/commit/db2ddb87143519e20a95aa36c60b36107b736a58)

### 2. 🔀 合并子系统树 trace-v7.2-rc6（08-09）
[查看提交](https://github.com/torvalds/linux/commit/b9b3e33b70b71e516930117e21de3ad2a7723747)

### 3. 🔀 合并子系统树 s390-7.2-7（08-09）
[查看提交](https://github.com/torvalds/linux/commit/b643e495ae92e2aa75a54c557a756e02f049781d)

### 4. 🔀 合并子系统树 x86-urgent-2026-08-08（08-08）
[查看提交](https://github.com/torvalds/linux/commit/06cf61899d6498b33e4b7c87d99d5bd471ccc375)

### 5. 🔀 合并子系统树 locking-urgent-2026-08-08（08-08）
[查看提交](https://github.com/torvalds/linux/commit/d4eee3bdb8af1010a0c1edf571c00a7f41c5abe3)

### 6. 🔀 合并子系统树 usb-7.2-rc7（08-08）
[查看提交](https://github.com/torvalds/linux/commit/91a73db6970aa7cd3d2ea73a4a11eeb3519737db)

### 7. 🔀 合并子系统树 tty-7.2-rc7（08-08）
[查看提交](https://github.com/torvalds/linux/commit/e4836b67bad62f10e142f8dd71e67473778de518)

### 8. 🔀 合并子系统树 staging-7.2-rc7（08-08）
[查看提交](https://github.com/torvalds/linux/commit/e663f6deac9d113d158eb0ba7433659fe4d95ade)

## ⏳ LTS / EOL 生命周期

| 产品 | 版本 | EOL 日期 | 状态 |
| --- | --- | --- | --- |
| [openssl](https://endoflife.date/openssl) | 3.0 LTS | 2026-09-07 | ⚠️ 仅剩 28 天 |
| [openssl](https://endoflife.date/openssl) | 3.4 | 2026-10-22 | ⚠️ 仅剩 73 天 |
| [openssl](https://endoflife.date/openssl) | 3.6 | 2026-11-01 | ⚠️ 仅剩 83 天 |
| [linux](https://endoflife.date/linux) | 5.15 LTS | 2026-12-31 | 📅 约 4 个月 |
| [linux](https://endoflife.date/linux) | 5.10 LTS | 2026-12-31 | 📅 约 4 个月 |
| [ubuntu](https://endoflife.date/ubuntu) | 22.04 LTS | 2027-04-01 | ✅ 约 7 个月 |

## 🔧 工具链更新

### 1. systemd v259.8（2026-07-24）
补丁版本，包含多项修复与更新，具体见变更日志。
📍 *来源：[systemd Releases](https://github.com/systemd/systemd/releases/tag/v259.8)*

### 2. containerd v2.3.3（2026-07-10）
2.3 系列第三个补丁版本，包含多项修复与更新；Windows 下设置 SystemTemp 环境变量以正确解析临时目录。
📍 *来源：[containerd Releases](https://github.com/containerd/containerd/releases/tag/v2.3.3)*

### 3. Docker Engine v29.7.2（2026-08-06）
补丁版本，针对 docker/cli 及引擎修复多项问题，完整变更见对应 milestone。
📍 *来源：[Docker Engine Releases](https://github.com/moby/moby/releases/tag/docker-v29.7.2)*

### 4. OpenSSL 4.0.1（2026-06-09）
安全补丁版本，修复最高严重级别为 High 的 CVE；包括 PKCS7_* 系列函数中的堆 use-after-free 漏洞。
📍 *来源：[OpenSSL Releases](https://github.com/openssl/openssl/releases/tag/openssl-4.0.1)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
