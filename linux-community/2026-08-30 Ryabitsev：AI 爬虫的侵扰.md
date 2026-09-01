# Linux 社区动态 | 2026.08.30

> 内核版本、安全通告、关键机制与 Linus 动态的每日速览。
> 📊 今日新增：文章 1 · Linus 4 · EOL 变化

## 🐧 内核版本动态

当前主线 [v7.2](https://github.com/torvalds/linux/tree/v7.2)，今日无新版本。

## 🛡️ 安全通告

_今日无新增安全通告。_

## 🔬 内核社区与关键机制

### 1. Ryabitsev：AI 爬虫的侵扰
git.kernel.org 每日约 600 万请求中 66% 被 Anubis 工作量证明拦截，但 33% 已能解算通过；宽松估算下合法请求仅占约 2%，其余全是爬虫。
📍 *来源：[LWN](https://lwn.net/Articles/1091203/)*
📅 2026-08-29

## 💻 Linus 动态

### 1. 🔀 合并子系统树 for-linus（08-29）
[查看提交](https://github.com/torvalds/linux/commit/08dbfad3f5040f5bdb6c529da20d6d4e81fefd72)

### 2. 🔀 合并子系统树 io_uring-7.3-20260828（08-28）
[查看提交](https://github.com/torvalds/linux/commit/cf72cbb39da84b6f02f90c07f33b102fc10b16f0)

### 3. 🔀 合并子系统树 drm-next-2026-08-29（08-28）
[查看提交](https://github.com/torvalds/linux/commit/a99d741df7372f2175677673d78a6335f3e0706f)

### 4. 🔀 合并子系统树 for-linus-7.3-1（08-28）
[查看提交](https://github.com/torvalds/linux/commit/4cc4cc367fd5c37ddef3279038bccbf152ef68d9)

## ⏳ LTS / EOL 生命周期

| 产品 | 版本 | EOL 日期 | 状态 |
| --- | --- | --- | --- |
| [openssl](https://endoflife.date/openssl) | 3.0 LTS | 2026-09-07 | ⚠️ 仅剩 8 天 |
| [openssl](https://endoflife.date/openssl) | 3.4 | 2026-10-22 | ⚠️ 仅剩 53 天 |
| [openssl](https://endoflife.date/openssl) | 3.6 | 2026-11-01 | ⚠️ 仅剩 63 天 |
| [linux](https://endoflife.date/linux) | 5.15 LTS | 2026-12-31 | 📅 约 4 个月 |
| [linux](https://endoflife.date/linux) | 5.10 LTS | 2026-12-31 | 📅 约 4 个月 |
| [openssl](https://endoflife.date/openssl) | 4.0 | 2027-05-14 | ✅ 约 8 个月 |

## 🔧 工具链更新

_今日无新 release。_

---

_本报告由 Hermes 自动生成 · Linux 社区动态_
