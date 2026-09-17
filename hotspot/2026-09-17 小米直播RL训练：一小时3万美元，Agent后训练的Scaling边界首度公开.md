**🔥 小米直播RL训练：一小时3万美元，Agent后训练的Scaling边界首度公开**

─── 【事件速览】 ───

9月17日凌晨（北京时间），小米 MiMo 负责人罗福莉在 X 结束近半年静默：MiMo-V2.6 正处于 RL 训练中，团队沿三条轴扩规模——计算量（约 2B tokens/step、1568 prompts × 16 rollouts、fully async）、环境与执行框架（multi-task agentic RL，多 harness 混入同一 run）、判分算力（agentic in-group credit assignment，test-case + rubric 奖励）。同步开放实时面板 mimo.xiaomi.com/rl，公开 step 进度、累计成本、token/样本量、采样通过率、critic reward、KL、staleness、batch composition 与 DeepSWE v1.1 结果，并公开故障通知与重启记录。

面板时间戳显示 Pro 于 9月15日 10:32 UTC 起跑、Flash 于 15:16 UTC 起跑，公开时已训练约两天。抓取快照：Pro 在 step 12/13、$849,485、25.1B tokens、301k 样本；Flash 在 step 15/16、$376,065、35.2B tokens；合计约 122.6 万美元，平均约 3.1 万美元/小时（折合约 20 万元人民币/小时）。DeepSWE v1.1：Pro 63.72、Flash 60.77。

─── 【为什么重要】 ───

预训练 Scaling 能成为方法论，是因为它有公认、可复现的验证方式：数据/参数/算力升，loss 降。RL 的 Scaling 一直没有这个待遇——它强依赖环境、奖励与采样配置，外部只能看到终版分数，看不到曲线形状、失败率和单位成本。把训练过程本身当发布物，等于把"后训练算力投入"从公关措辞变成可连续追踪的公开账本。

科研层面：过程公开让"RL 还能 scale 多远"从观点之争变成数据之争，外部研究者第一次能用真实量级校准自己的实验预算与预期。产业层面：Agent 基座竞争的主战场正在从"发榜单"转向"发流程"，因为榜单可被质疑污染，而流程更难伪造；这同时是给人才市场与资本市场的技术信誉押注。工程层面：它把 RL 的真实瓶颈暴露出来——不是 GPU 不够，而是环境并发、判分吞吐、错误检测和 off-policy 数据管理跟不上。

─── 【架构师解读】 ───

一、被 scaled 的不是模型，是"经验生产系统"。三条轴的本质分工很清楚：compute 决定每轮能探索多少条轨迹，environment/harness 决定经验分布有多宽，grader compute 决定这些经验里有多少能转成有效梯度。面板把三者同时量化了：Pro 单步 2.33B tokens，步时 2h31m（其中外层生成 1h27m、训练器 1h00m）；env/active 为 Pro 2.4 万、Flash 3.8 万个并发环境；batch composition 中 code 占 67.3%、visual 13.0%、general 12.0%、cyber 4.8%、chat 3.0%，共 25 个数据源。这意味着它的"环境"是一批并行运行、带工具与判分的沙箱集群——能力来自几万个同时展开的真实任务世界，不是来自权重里的知识。

二、公开数据里最值钱的不是奖励曲线，是信噪比。Pro 的 critic/rewards/mean 从 0.55 抬到 0.582、Flash 从 0.52 到 0.570，涨幅只有 3–5 个百分点，且单步内还会回落。对照采样侧指标：passrate/zero = 15.1%（整组全失败），passrate/one 约 23–25%（一组里只有一条通过）。按组相对优势类方法（如 GRPO）的通行语义，这两类组的组内方差趋近于零，优势信号几乎没有信息量——接近四成的采样算力生产的是"无法学习的经验"。这才是 grader compute 必须同步扩的真正原因：不是让判分更准，而是要在同一 prompt 的 16 条轨迹之间做可分辨的贡献归因，把"全错"和"只对一条"变成有梯度的信号。

三、异步是有价格的。面板里 partial/avg_staleness：Pro 0.678、Flash 1.87；对应的 new_infer/kl 为 0.00656 与 0.00833，而 Flash 外层生成只要 58m（Pro 1h27m）。fully async 用 on-policy 纯度换吞吐，Flash 实际上在用近两个 step 之前的数据训练。走异步 RL 的团队应把 staleness 当显式超参而非意外，并把它与 KL、熵（actor/entropy_loss 0.432 vs 0.392）联动监控。

四、最贵的是静默错误。面板通知写着两件事：Pro 因单节点 VRAM 问题重启；Flash 从 step 15 重启，原因是"某数据集的 infra 错误在过去约 3 小时未被正确检出"。而 infra_error/seq_rate 只有 0.45%–0.51%——错误率极低，漏检一次就是按小时计的钱。更值得注意的是成本计数器与进度计数器解耦：Flash 重启后 step 与累计 token 回退，cost 只增不减。RL 规模化的核心工程能力，正从"调算法"转向"检测环境与数据异常并快速止损"。

五、不吹的部分：过程公开不等于可复现。环境是自家的、reward 是自家的、grader 也是自家的，DeepSWE 用的是自选配置（mini-swe-agent，avg@3），三条轴的具体配比与 credit assignment 算法尚未公布。外部目前能对齐的只是量级基线：天级训练、2B tokens/step、百万美元预算、每 step 数万美元。对国内团队更现实的读法是——小米此前已用性价比与真实 Agent 基准卡位，这次直播是"过程透明 + 极致性价比"组合拳的延续，用可信流程换生态位，而非用单个榜单换声量。风险也在同一处：中途公开意味着没有悄悄回滚的空间，掉点、重启、超支都会留在公开记录里。

─── 【对从业者的启示】 ───

1. 先建观测，再谈算法。把环境/判分的错误检测、通过率分布、staleness 做成一级看板。这类止损能力的 ROI 高于任何新的 reward 设计。

2. 用信噪比做算力预算。盯住 passrate/zero 与 passrate/one，对无梯度组做动态采样或难度过滤，否则近四成 rollout 是纯消耗。

3. 环境与判分是资产，不是脚手架。harness、rubric、test-case 会跨模型代际沉淀；权重会被下一代超越，评测资产不会。

4. 异步程度必须显式定价。staleness 越大吞吐越高、on-policy 纯度越低，要和 KL、熵一起调，别把它当成隐含 bug。

5. 读这份直播要读失败项。重启原因、infra error、offline 评测延迟，这些是论文与宣传稿里不会出现的真实成本结构。

─── 【参考来源】 ───

📍 来源：[罗福莉 X 帖文](https://x.com/_luofuli/status/2100296686719610932)
📍 来源：[MiMo-V2.6 实时 RL 训练面板](https://mimo.xiaomi.com/rl/)
📍 来源：[量子位](https://www.qbitai.com/2026/09/490950.html)
📍 来源：[网易科技·AppSo](https://www.163.com/dy/article/L71BNN3E0511CSAO.html)