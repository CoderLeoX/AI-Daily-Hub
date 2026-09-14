# AI 前沿资讯日报 | 2026.09.15 — OpenAI / Google

> 📋 每日 AI 前沿资讯一览。

## 📌 AI 前沿资讯

📌 今日 AI 领域共 16 条值得关注的动态，核心关键词：OpenAI、NVIDIA、AI Agent。详情如下：

导读

## 今日最重要 3 条

### 1. Perplexity 便携计算机登陆 Windows，由 NVIDIA RTX 驱动

**核心**：随着本地模型能力提升，AI Agent 可以在 PC 上直接处理更多工作，同时把敏感信息留在设备内。Portable Computer 是 Perplexity 旗下 Agent 的本地版本。
**工程影响**：端侧 Agent 的算力基线正从云端下沉到 RTX 级本地硬件，隐私敏感场景有了可落地的本地推理路径。

📍 来源：[NVIDIA](https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/)

### 2. NVIDIA 开源 OSMO

**核心**：NVIDIA 开源了 Kubernetes 原生工作流编排器 OSMO，它在内部用于 Project GR00T、Isaac Lab 与 Isaac Sim。OSMO 让机器人团队能够定义训练、仿真与硬件相关流程。
**工程影响**：机器人训练与仿真流水线有了 Kubernetes 原生编排底座，团队可直接复用 NVIDIA 内部同款基础设施。

📍 来源：[MarkTechPost](https://www.marktechpost.com)

### 3. Perplexity 用 GPT-6 Astra 接管端到端系统

**核心**：Perplexity 使用 Astra 撰写对外沟通内容、修改软件、监控生产系统，且相较更早的模型，检查核对的频次大幅降低。
**工程影响**：前沿模型开始承担生产系统的端到端职责，验证与回滚机制随之成为关键风险面。

📍 来源：[OpenAI](https://openai.com/index/perplexity-improving-accuracy-with-astra)

## 模型 / 研究

### 1. 首届蚂蚁灵波具身大模型挑战赛正式启动

**核心**：蚂蚁灵波希望借这场大赛，把 LingBot-VLA 推向更广泛的开发者社区与高校科研社区。
**工程影响**：VLA 能力走的是开源加赛事扩散路线，具身智能的人才与工具入口被前置到高校。

📍 来源：[量子位](https://www.qbitai.com/2026/09/489105.html)

### 2. 探索 RSI，生数新世界模型让机器人开始自我进化

**核心**：生数的新世界模型探索 RSI，让机器人具备自我进化能力。
**工程影响**：世界模型叠加自我改进闭环，是从数据驱动转向自生成数据驱动的关键一步。

📍 来源：[量子位](https://www.qbitai.com/2026/09/489037.html)

## Agent / 工具

### 1. Agent Harness、Agent Framework 与 MCP：哪一层拥有循环、状态与工具

**核心**：一份实践者视角的现代 Agent 技术栈三层地图，附可核验来源与重叠度分析，文章本身就在追问这三层分别由谁掌管 Loop、State 与 Tools。
**工程影响**：选型时先分清 harness、framework、协议三层的职责边界，避免把编排逻辑绑死在错误的抽象上。

📍 来源：[MarkTechPost](https://www.marktechpost.com)

### 2. DevFest 2026 回归

**核心**：DevFest 2026 回归，全球 800 多场活动，主题聚焦 Agentic AI 时代的构建、安全与规模化。
**工程影响**：Agentic AI 已成为主流开发者活动的默认议题，社区侧人才供给会加速跟进。

📍 来源：[Google AI](https://blog.google/innovation-and-ai/technology/developers-tools/devfest2026/)

### 3. 不下班的经营者：把 LLM-as-Judge 做成会自我校准的评估闭环｜QCon 上海

**核心**：QCon 上海议题，讲解如何把 LLM-as-Judge 做成一个会自我校准的评估闭环。
**工程影响**：评估环节从一次性打分升级为自我校准闭环，这是 LLM 应用进入生产的前置条件。

📍 来源：[InfoQ](https://www.infoq.cn/article/LoKvL75PL8g48hD3UNCE?utm_source=rss&utm_medium=article)

### 4. Sakana AI 发布 PC-ALM：反向传播的层局部替代方案，可训练 1000 层网络

**核心**：Sakana AI 研究者 Jeffrey Seely 与 Julian Gould 提出增广拉格朗日预测编码（PC-ALM），作为反向传播的局部学习替代方案，做法是给预测编码引入拉格朗日乘子。
**工程影响**：局部学习若能在 1000 层网络上成立，将改变超深网络的训练内存占用与并行策略。

📍 来源：[MarkTechPost](https://www.marktechpost.com)

## 产业 / 公司

### 1. NVIDIA 与 SpaceXAI 把 Grok 扩张与轨道计算绑定

**核心**：报道称 NVIDIA 与 SpaceXAI 将 Grok 的扩张与轨道计算联系起来。
**工程影响**：算力基础设施的选址边界可能从地面扩展到在轨场景。

📍 来源：[The Futurum Group](https://futurumgroup.com)

### 2. openJiuwen 首发双维度 RSI 框架：AI 自修改、落地办公智能体、算力亲和

**核心**：openJiuwen 首发双维度 RSI 框架，支持 AI 自我修改，落地办公智能体，并强调算力亲和，做到又快又省。
**工程影响**：RSI 框架切入办公智能体场景，算力亲和成为自改进系统能否落地的硬约束。

📍 来源：[InfoQ](https://www.infoq.cn/article/JghIFNXBNVSAfbgbR4S9?utm_source=rss&utm_medium=article)

### 3. 马斯克旗下公司撤销对苹果的反垄断诉讼，继续针对 OpenAI

**核心**：马斯克旗下公司撤回针对苹果的反垄断诉讼，但对 OpenAI 的诉讼继续进行。
**工程影响**：诉讼焦点收敛到 OpenAI，竞争从产品层延伸到司法与监管层。

📍 来源：[PYMNTS.com](https://www.pymnts.com)

## 领军人物动向

### 1. 马斯克把苹果移出 AI 反垄断诉讼，火力继续对准 OpenAI

**核心**：Elon Musk 将 Apple 从 AI 反垄断诉讼中移除，同时继续针对 OpenAI。
**工程影响**：战线收缩意味着指控更集中，OpenAI 在监管与舆论层面的压力随之上升。

📍 来源：[stocktwits.com](https://stocktwits.com) · [PYMNTS.com](https://www.pymnts.com)

### 2. 马斯克对 SpaceX、英伟达股价释放强烈信号

**核心**：报道称马斯克对 SpaceX 与英伟达股价给出强烈信号。
**工程影响**：马斯克相关表态持续影响算力与航天板块的市场预期。

📍 来源：[thestreet.com](https://www.thestreet.com)

### 3. 一边撤诉一边继续开战：马斯克放弃起诉苹果反垄断，仍要追究 OpenAI 责任

**核心**：马斯克放弃对苹果的反垄断起诉，同时表示仍要追究 OpenAI 的责任。
**工程影响**：同一诉讼链条上的取舍，反映其对主战场优先级的重新排序。

📍 来源：[news.mydrivers.com](https://news.mydrivers.com)

### 4. 马斯克强调他最早敲响 AI 警钟

**核心**：马斯克在 X 上发帖，提醒外界他是最早发出 AI 警报的人；此时 Anthropic 与 OpenAI 高管也在表达对前沿模型失控的同类担忧。
**工程影响**：头部厂商高管在失控风险上形成话语共振，将影响后续监管议题的走向。

📍 来源：[Yahoo Finance Singapore](https://sg.finance.yahoo.com) · [Yahoo Finance](https://finance.yahoo.com)

## 架构师判断

• NVIDIA 是今天最集中的信号来源。
• 今天更值得注意的，不只是单点模型能力，而是模型与研究能力正在更直接地进入真实工作流。
• AI 工具竞争的重点，正在从"能不能用"继续转向"能不能稳定进入真实生产流程"。
• 除了产品更新，基础设施、企业落地或平台竞争也在同步推进，行业竞争仍在加速展开。

附注：本次抓取未成功的数据源有：36Kr。
统计口径：优先采用近 24 小时公开信息，不足时以近 72 小时补位。

两点需要你确认：素材中 MarkTechPost、PYMNTS.com、stocktwits.com、thestreet.com、news.mydrivers.com 这类来源只给了站点首页，原抓取未保留具体文章 URL，我按原样保留未做拼接（凭空补路径会造出死链）。另有两处摘要被抓取截断（Perplexity 本地版 Agent 名称、OSMO 的能力描述后半句、PC-ALM 的公式细节），我只写到了原文可见范围内，没有补全。

---

_本报告由 Hermes 自动生成 · AI 前沿资讯日报_