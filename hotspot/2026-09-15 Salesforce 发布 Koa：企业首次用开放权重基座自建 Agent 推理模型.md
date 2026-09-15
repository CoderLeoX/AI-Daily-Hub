**🔥 Salesforce 发布 Koa：企业首次用开放权重基座自建 Agent 推理模型**

─── 【事件速览】 ───

9 月 15 日，Dreamforce 2026，Salesforce 联合 NVIDIA 发布 Koa——Salesforce 首个自研推理模型。底座是 NVIDIA 3 月开源的 Nemotron-3-Super-120B（120B 总参 / 12B 激活，LatentMoE 混合 Mamba-Transformer，1M 上下文，NVFP4 预训练）。

Salesforce 用 SFT + GRPO 强化学习做后训练，训练语料全部为合成数据与公开数据，官方明确声明未使用任何客户数据。arXiv 同期论文（2609.15066）公开方法：把声明式 Agent 规格（Agent Script）展开为 persona 条件化的多轮任务，以"工具调用真正成功"作为 grounded reward 驱动 GRPO。

官方数据：CRM Bench 上动作调用准确率 +11%、上下文回忆 2.1 倍、长对话记忆 +15%、错误率降 3 倍；但论文自认"超过一个强商业基线（GPT-4.1），仍低于最强前沿模型"。Koa 已在 Salesforce 内部 Slack 员工 Agent 上线，试点客户含 Formula 1、Xero、UChicago Medicine、Baxter Credit Union 等，GA 定档 2026 冬季美国区域。

─── 【为什么重要】 ───

在 Koa 之前，Agentforce 里凡是需要多步推理的请求，都被 AI 网关路由到 Claude 或 ChatGPT。Koa 的意义在于：把一个企业最高的推理支出、最重的上下文、最敏感的数据流，从外部前沿 API 收回自有信任边界。

三层含义。一是模型网关的定位变了，从"选哪家 API"变成"哪些推理不许出边界"，网关从接入层升级成控制面。二是成本结构变了，token 外付变成内部 GPU 折旧，账期与单位经济都不一样。三是选型标准多了一条硬约束：基座数据来源可溯（data provenance）。Salesforce 的 Govindarajan 直接点名"我们不知道 Qwen 训练了什么"，这是把数据来源、许可、司法辖区抬进了采购清单。

同时注意一个反向信号：Salesforce 并未放弃前沿模型，同期还宣布了 ClaudeForce。这不是替代，是分层。

─── 【架构师解读】 ───

真正有技术含量的不是模型，是数据生产线。Koa 的可复用点是 spec→reward：用声明式 Agent 规格自动生成 persona 条件化的多轮任务，reward 锚定在"data-dependent 请求是否真的成功调用了工具"，而不是让模型自评。这意味着企业内部的流程定义——Flow、Agent 配置、工单 SOP——第一次成了可规模化的 RL 训练信号。领域模型过去卡在"标注数据从哪来、客户数据不敢用"，Koa 给出的答案是：从工作流规格里合成，绕开合规红线。

成本账要重算。Agent 的账单不是单价 × token，而是回合数 × 上下文重放：多轮 tool use 每轮都要重放历史，消耗近似二次增长。Koa 削减错误调用（3x fewer errors）并更快收敛到任务完成，直接减少回合数——这才是"更省 token"的真实来源，而不是单价便宜。NVIDIA 强调 LatentMoE + MTP，本质是为了 12B 激活的推理吞吐，配合的是高频高量场景，不是难题场景。

但别被"open-weight"误导。NVIDIA 开的是基座（权重、数据、配方），Koa 自己不开权重：权重在 Salesforce 手里，只跑在 Salesforce 基础设施内，以 managed LLM 交付，组织级/Agent 级/子 Agent 级三档可选，并且托管在 temperature 0。结论很直接——客户拿到的是合规证明和一致性，不是自托管能力。锁定只是从"前沿 API 锁定"换成"平台托管模型锁定"，议价权的形状没变，只是换了甲方。

Provenance 是采购条款，不是技术指标。客观看 NVIDIA 自己公布的对比表里，Nemotron-3-Super 在 agentic 细分并非全面领先 Qwen3.5-122B：TauBench Telecom 64.36 对 95.00，Terminal Bench Core 2.0 为 31.00 对 37.50，MMLU-Pro 83.73 对 86.70。可溯源是加分项，代价可能是某些基准上的让步，两者要一起接受。

还有两处要打折扣。其一，CRM Bench 是 Salesforce 自建、自己跑、自己公布的指标，客户试点反馈目前仍是证言级证据；GA 未到、美区优先、开放 beta 更晚——非美区与受监管行业的可用性只能按季度做路线图假设。其二，Agentforce 按 Flex Credit 计费，模型换代带来的内部成本下降不会自动传导到客户账单，除非合同写明。这类"平台侧省成本、账单侧不动"的结构，值得在续约谈判里单独列项。

─── 【对从业者的启示】 ───

一、先量自己的 token 结构。把单任务回合数、上下文重放量、重试率打点出来，再谈换不换模型。多数团队的浪费在回合数上，不在模型单价上。

二、把声明式工作流当资产。流程定义、工单 SOP、Agent 配置规格化之后，就是你的合成数据源。这是 Koa 最值得抄的一步，成本远低于自建推理模型。

三、模型网关按子 Agent 粒度做路由表、预算上限和回退链。Koa 能按 org/agent/sub-agent 三档选型，说明"全局一个模型"的网关设计已经过时。

四、选型时把 provenance、许可、司法辖区写进条款，同时用自己的任务集复现供应商的 benchmark。厂商自建榜、自报数字，只能当线索不能当验收。

五、合成数据 + 小模型 RL 是可在小规模复制的实验。挑 2–3 类高频多步任务，用开源基座跑一轮 GRPO，先验证收益曲线，再决定是否上专用推理模型。同一周内 Agent 开始直接调用基础设施的讨论也在升温，控制面的竞争才刚开始。

─── 【参考来源】 ───

📍 *来源：[TechCrunch](https://techcrunch.com/2026/09/15/salesforce-and-nvidias-new-reasoning-model-is-everything-the-ai-labs-should-fear/)*
📍 *来源：[SiliconANGLE](https://siliconangle.com/2026/09/15/salesforce-debuts-koa-a-specialized-model-built-to-reason-over-crm-data/)*
📍 *来源：[ITPro](https://www.itpro.com/technology/artificial-intelligence/salesforce-teams-up-with-nvidia-to-launch-koa-a-dedicated-crm-reasoning-model)*
📍 *来源：[Salesforce Koa 官方页](https://www.salesforce.com/agentforce/koa/)*
📍 *来源：[arXiv 2609.15066](https://arxiv.org/abs/2609.15066)*
📍 *来源：[NVIDIA Nemotron 3 Super 模型卡](https://build.nvidia.com/nvidia/nemotron-3-super-120b-a12b/modelcard)*
📍 *来源：[InfoQ 中文](https://www.infoq.cn/article/jGTsO1DrV87muOqyDPGS)*