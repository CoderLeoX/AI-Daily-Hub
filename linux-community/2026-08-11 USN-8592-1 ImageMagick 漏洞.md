# Linux 社区动态 | 2026.08.11

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

### 1. USN-8592-1: ImageMagick 漏洞
Hao Ren 发现 ImageMagick 在使用 wavelet-denoise 操作处理特定图像时校验不当，攻击者可触发越界堆写入，可能导致任意代码执行。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8592-1)*
📅 2026-08-11

### 2. USN-8626-1: systemd 漏洞
systemd-homed 未正确验证 home 记录签名，本地攻击者可向已登录用户添加任意系统组，从而实现权限提升。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8626-1)*
📅 2026-08-10

### 3. USN-8620-3: Linux 内核 (Intel IoTG) 漏洞
Maxim Suhanov 发现内核 NTFS 实现在特定情况下未正确校验文件名长度，导致越界读取，攻击者可借此泄露敏感信息或造成拒绝服务（系统崩溃）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8620-4)*
📅 2026-07-31

### 4. USN-8620-4: Linux 内核 (Intel IoTG) 漏洞
Maxim Suhanov 发现内核 NTFS 实现在特定情况下未正确校验文件名长度，导致越界读取，攻击者可借此泄露敏感信息或造成拒绝服务（系统崩溃）。
📍 *来源：[Ubuntu Security](https://ubuntu.com/security/notices/USN-8620-3)*
📅 2026-07-31

### 5. DSA-6428-1 libyaml-syck-perl 安全更新
Debian 已发布 libyaml-syck-perl 安全更新，修复相关安全漏洞。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00339.html)*

### 6. DSA-6427-1 wordpress 安全更新
Debian 已发布 wordpress 安全更新，修复相关安全漏洞。
📍 *来源：[Debian Security](https://lists.debian.org/debian-security-announce/2026/msg00338.html)*

## 🔬 内核社区与关键机制

### 1. 为 BPF 做更多形式化验证
BPF 已提供有用的安全保证，但 Kumar Kartikeya Dwivedi 希望 BPF 程序更安全；在 2026 Linux 存储、文件系统、内存管理与 BPF 峰会上，他主持了相关讨论。
📍 *来源：[LWN](https://lwn.net/Articles/1087069/)*
📅 2026-08-10

### 2. 内核预发布版 7.2-rc7
7.2-rc7 预发布版已推出供测试，体积仍比 Linus 期望的大，但他表示目前看不出推迟 7.2 正式版发布的理由。
📍 *来源：[LWN](https://lwn.net/Articles/1087961/)*
📅 2026-08-10

### 3. 四个周末稳定版内核更新
7.1.8、6.18.44、6.12.103 和 6.6.151 稳定版内核已发布，每个都包含大量重要修复。
📍 *来源：[LWN](https://lwn.net/Articles/1087949/)*
📅 2026-08-10

### 4. 周五稳定版内核：仅一个 bug 修复
Greg Kroah-Hartman 宣布发布 6.12.102、6.6.150、6.1.182、5.15.215、5.10.264 稳定版内核；本轮仅包含单个 bug 修复。
📍 *来源：[LWN](https://lwn.net/Articles/1087743/)*
📅 2026-08-07

### 5. 六个稳定版内核附带安全修复
Greg Kroah-Hartman 宣布发布 7.1.7、6.18.43、6.6.149、6.1.181、5.15.214、5.10.263 稳定版内核，修复一个安全漏洞（CVE-2026-68480）。
📍 *来源：[LWN](https://lwn.net/Articles/1087567/)*
📅 2026-08-07

### 6. 将 BPF 引入 binfmt_misc
内核能运行多种可执行文件，包括 ELF 原生二进制和以 #! 开头的解释型脚本；此外它还有一个名为 binfmt_misc 的机制，可扩展可执行格式支持。
📍 *来源：[LWN](https://lwn.net/Articles/1086947/)*
📅 2026-08-06

## 💻 Linus 动态

### 1. 🔀 合并子系统树 regmap-fix-v7.2-rc7（08-10）
[查看提交](https://github.com/torvalds/linux/commit/d58772d8520c7ef247c4b95c9bd76d3a25da9ff5)

### 2. 🔀 合并子系统树 v7.2-p3（08-10）
[查看提交](https://github.com/torvalds/linux/commit/5eabf07a0bf317723da229376b4e910f12b4644b)

### 3. 🏷️ 版本发布 Linux 7.2-rc7（08-09）
[查看提交](https://github.com/torvalds/linux/commit/db2ddb87143519e20a95aa36c60b36107b736a58)

### 4. 🔀 合并子系统树 trace-v7.2-rc6（08-09）
[查看提交](https://github.com/torvalds/linux/commit/b9b3e33b70b71e516930117e21de3ad2a7723747)

### 5. 🔀 合并子系统树 s390-7.2-7（08-09）
[查看提交](https://github.com/torvalds/linux/commit/b643e495ae92e2aa75a54c557a756e02f049781d)

### 6. 🔀 合并子系统树 x86-urgent-2026-08-08（08-08）
[查看提交](https://github.com/torvalds/linux/commit/06cf61899d6498b33e4b7c87d99d5bd471ccc375)

### 7. 🔀 合并子系统树 locking-urgent-2026-08-08（08-08）
[查看提交](https://github.com/torvalds/linux/commit/d4eee3bdb8af1010a0c1edf571c00a7f41c5abe3)

### 8. 🔀 合并子系统树 usb-7.2-rc7（08-08）
[查看提交](https://github.com/torvalds/linux/commit/91a73db6970aa7cd3d2ea73a4a11eeb3519737db)

## ⏳ LTS / EOL 生命周期

| 产品 | 版本 | EOL 日期 | 状态 |
| --- | --- | --- | --- |
| [openssl](https://endoflife.date/openssl) | 3.0 LTS | 2026-09-07 | ⚠️ 仅剩 27 天 |
| [openssl](https://endoflife.date/openssl) | 3.4 | 2026-10-22 | ⚠️ 仅剩 72 天 |
| [openssl](https://endoflife.date/openssl) | 3.6 | 2026-11-01 | ⚠️ 仅剩 82 天 |
| [linux](https://endoflife.date/linux) | 5.15 LTS | 2026-12-31 | 📅 约 4 个月 |
| [linux](https://endoflife.date/linux) | 5.10 LTS | 2026-12-31 | 📅 约 4 个月 |
| [ubuntu](https://endoflife.date/ubuntu) | 22.04 LTS | 2027-04-01 | ✅ 约 7 个月 |

## 🔧 工具链更新

### 1. systemd v259.8（2026-07-24）
例行补丁版本，修复 v259.7 以来的若干缺陷，无新增功能。
📍 *来源：[systemd Releases](https://github.com/systemd/systemd/releases/tag/v259.8)*

### 2. containerd v2.3.3（2026-07-10）
2.3 系列第三个补丁版，包含多项修复与更新，如 Windows 下设置 SystemTemp 环境变量。
📍 *来源：[containerd Releases](https://github.com/containerd/containerd/releases/tag/v2.3.3)*

### 3. Docker Engine docker-v29.7.2（2026-08-06）
29.7.2 补丁版，包含 docker/cli 与 engine 的多项修复和变更。
📍 *来源：[Docker Engine Releases](https://github.com/moby/moby/releases/tag/docker-v29.7.2)*

### 4. OpenSSL openssl-4.0.1（2026-06-09）
安全补丁版，修复的最高严重级别 CVE 为 High，含 PKCS7 相关函数的堆释放后使用问题。
📍 *来源：[OpenSSL Releases](https://github.com/openssl/openssl/releases/tag/openssl-4.0.1)*

### 5. curl 8.21.0（2026-06-24）
例行版本更新，修复多个缺陷，完整变更见 changelog。
📍 *来源：[curl Releases](https://github.com/curl/curl/releases/tag/curl-8_21_0)*

### 6. Podman v6.0.2（2026-07-22）
修复 Windows 下 WSL provider 创建的 podman machine VM 在 init 失败时未正确清理的问题。
📍 *来源：[Podman Releases](https://github.com/podman-container-tools/podman/releases/tag/v6.0.2)*

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
