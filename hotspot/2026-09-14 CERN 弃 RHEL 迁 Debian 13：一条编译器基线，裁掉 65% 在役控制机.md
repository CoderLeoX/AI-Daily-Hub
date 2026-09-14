**🔥 CERN 弃 RHEL 迁 Debian 13：一条编译器基线，裁掉 65% 在役控制机**

─── 【事件速览】 ───

2026 年 8 月底，CERN 工程师 Federico Vaga 与 Nikos Tsipinakis 在瑞士 MiniDebConf Winterthur 上披露：CERN 加速器控制系统的前端机队将整体迁往 Debian 13（Trixie），目标 2026 年第四季度完成，目前已有数十台进入生产。

规模是 2200 余台工业前端计算机与约 1.7 万台嵌入式设备，分布在地下约 43 平方公里的隧道与设备厅。触发点不是许可证费用，而是 Red Hat 的编译器微架构基线：RHEL 9 要求 x86-64-v2（SSE4.2、POPCNT），RHEL 10 抬到 x86-64-v3（AVX2、BMI、FMA）。CERN 测算 v2 会淘汰 47% 的在役嵌入式控制机，v3 在剩余的机器里再淘汰 17%，合计约 65%。硬扛的代价是重新设计 11 块定制板卡、增编 2 名电子工程师 + 2 名软件工程师 + 2 名技师、部分点位需重挖 100 米深的隧道，估算至少 540 万瑞郎，且成功率仅约 20%。

范围必须说清：迁移只覆盖加速器控制的嵌入式与工业前端层，Tier-0 网格、PB 级数据中心与实验计算仍留在 RHEL 与 AlmaLinux。CERN 同时开始赞助 Freexian 的 Debian ELTS 服务，并顺带重写了沿用自 2005 年的引导栈。

─── 【为什么重要】 ───

这件事的分量不在「CERN 换发行版」，而在于它暴露了一个长期被忽略的事实：硬件的实际生命周期，正被一个编译期常量裁决。

微架构基线不是性能档位，而是准入门槛。落到 v2/v3 之下的机器不是跑得慢，是根本起不来。CERN 的机队是焊在超导磁体旁边的设备——2011 年上线、无故障运行至今、设计寿命 10 到 15 年，与加速器长停机窗口对齐。这类设备的退役决定权，本该属于物理学家和维修预算，而不是上游 `-march` 的默认值。

第二重意义在于，这是 CentOS 8 事件之后 Red Hat 生态最具可见度的流失。CERN 曾是 Scientific Linux 的共同维护者、CentOS 的背书方，是「企业级 Linux 的样板客户」。样板客户因为一个编译器默认值出走，比任何竞品营销都更能说明问题。对国内大量停留在 CentOS 7/8、靠 AlmaLinux 续命的基础设施团队，这是一个可复用的决策样本。

─── 【架构师解读】 ───

我认为最有价值的一层，是 CERN 放弃了「单一 OS 标准」这条坚持了二十年的架构信条。

加速器控制系统原本分三层：控制室客户端、高可用服务器中间层、地下实时前端层。2022 年评估后，RHEL 9 被选定用于服务器与控制台（支持到 2032 年），而嵌入式前端被单独拆出来走另一条路线。这不是妥协，是分级治理：服务器层的价值在于企业支持带来的回滚、认证和一致性；前端嵌入式层的价值在于硬件寿命与发行版寿命的对齐，以及不开挖隧道。

任何大型机队都该抄这个作业。单一标准是运维效率的优化手段，不是架构原则。当某一层的硬件寿命远长于发行版的寿命，强行统一标准会把效率优势变成技术债。

第二个判断：AlmaLinux 并不是没得选，CERN 仍然选了 Debian。AlmaLinux 10 提供了 x86-64-v2 的构建，正是为被 RHEL 10 抛弃的硬件准备的。但 CERN 工程师在现场被问到时明确表示，决策当时 AlmaLinux 项目无法就这项支持作出承诺——支持不只是编译出二进制，背后是大量测试与验证工作量。真正把 CERN 推走的，是「十年内两次依赖他人下游重建物」的概率。对一个必须规划 15 年周期的机构来说，独立于上游节奏的可预测性，比省下的迁移工时更值钱。

第三，PREEMPT_RT 合入 Linux 主线（6.12）是这次迁移的技术使能条件。加速器控制要求低延迟调度，过去这份能力要靠企业发行版的专用实时内核。上游把实时性做进主线之后，Debian 免费继承了这份能力。这揭示了一条趋势：商业发行版过去靠「把上游能力工程化、认证、兜底」建立护城河，当上游把能力直接做进主线，护城河会持续变窄。付费的正当性会越来越集中在长周期兜底与合规证明上，而不是功能领先。

第四，别把迁移想成换内核。CERN 自己承认了两处硬伤：Debian 缺少 RPM 生态那样成熟的批量打包与发布工具链，同一包多版本共存的支持在工具链各处不一致；自研硬件的内核驱动需要剥离多年在 RHEL 上累积的发行版特化假设。这套机队是网络引导 + NFS 根文件系统，内核、initramfs、引导器全部自建，镜像还要版本化。换句话说，迁移账单里 OS 本身占小头，构建、发布、版本治理体系的重建才是大头。

顺带被重写的引导栈值得单独一提。2005 年的 NFS + tftpd 模型被替换为：引导器、内核、initramfs、用户空间解耦为独立组件，由 Kubernetes 分发，reconciler 控制器持续对账期望态与实际态，漂移即自动重部署。这是把声明式配置管理与控制器模式下沉到内核与引导层——对 2200 台无盘边缘节点，手工推文件的时代该结束了。

最后是 Freexian 这条线。CERN 出钱赞助 Debian  ELTS，本质是给机队买寿险，而不是买 SLA。按 Freexian 公开口径，Trixie 的延展支持可到 2035 年 6 月。但要清醒：ELTS 不是全包，只覆盖订阅客户实际使用的包子集，架构也以 amd64 为主。想借 ELTS 兜底十年，前提是你先把依赖清单收窄、并跑得通「哪些包未被支持」的检测。这笔账应该在选型时就列进去，而不是等 EOL 前夜。

─── 【对从业者的启示】 ───

1. 把微架构基线写进硬件采购与刷新预算。RHEL 10 的 x86-64-v3 已在虚拟化集群上造成实际安装失败。选 CPU 时问一句：这块板子能撑到哪个发行版的哪个大版本。

2. 发行版选型按机队分层，不要用一个标准覆盖所有层。服务器层买企业支持，长寿命嵌入式层买发行版长寿与架构基线承诺。两层用两套策略，比统一后集体迁移便宜。

3. 把「能否自建并控制内核、initramfs、引导链」当作可迁移性的核心能力。CERN 能做这次切换，是因为它本来就不依赖发行版的默认引导。这项能力平时没用，换轨时决定生死。

4. 供应商锁定按切换成本计价，不按订阅费计价。540 万瑞郎不是 Red Hat 的报价，是切换成本。做年度评估时，把「上游政策变动导致的一次性迁移成本」单独列一行。

5. 若考虑用 LTS/ELTS 兜底长周期，先核包清单。确认订阅覆盖你实际依赖的每一个包、每一个架构，并建立「未被支持包」的自动化检测，别在 EOL 前一个月才发现缺口。

─── 【参考来源】 ───

📍 *来源：[InfoQ：CERN Renounces RHEL in Favor of Debian for Its Accelerator Controls Infrastructure](https://www.infoq.com/news/2026/09/cern-debian-infra/)*

📍 *来源：[The Register：CERN moves thousands of accelerator control computers to Debian](https://www.theregister.com/os-platforms/2026/09/03/cern-moves-thousands-of-accelerator-control-computers-to-debian/5294312)*

📍 *来源：[CERN：Selecting a Linux Operating System for CERN Accelerator Controls](https://inspirehep.net/files/f6eb491e9c8ebb207b1e10f68168c7f0)*

📍 *来源：[byteiota：CERN Ditches Red Hat for Debian 13: The CHF 5.4M Decision](https://byteiota.com/cern-ditches-red-hat-debian-13-migration)*

📍 *来源：[Hardware Busters：CERN's Debian Migration Moves 2,200 Accelerator Control Machines Off Red Hat](https://hwbusters.com/news/cerns-debian-migration-moves-2200-accelerator-control-machines-off-red-hat/)*

📍 *来源：[Freexian：Debian Extended LTS](https://www.freexian.com/lts/extended)*

正文约 2100 字。有两点做了口径取舍：一是迁移动机不写"许可证成本"，公开材料里 RHEL 订阅费并非主因，主因是微架构基线与硬件替换预算；二是补了 AlmaLinux 已提供 x86-64-v2 构建这一点，避免读者误以为 CERN 别无选择。