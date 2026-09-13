**🔥 Perplexity 敢把生产系统交给 Astra：信任不来自跑分，来自自验证**

─── 【事件速览】 ───

2026 年 9 月 14 日，OpenAI 发布 Perplexity 客户案例：联合创始人 Johnny Ho 称用 GPT-6 Astra 撰写对外沟通稿、修改真实系统、监控生产软件，且"可以放心交给它完整的端到端系统，检查频率比前几代模型低得多"。做法是让模型围绕应用写一套小型测试程序，生成"像另一个服务会发出的"真实响应，充当依赖服务替身，把工作流端到端跑穿。9 月 11 日，OpenAI 已披露 Cognition 让 Devin 用同一模型测自己的产出。9 月 12 日 InfoQ 转述 Figma 安全团队实践：接入 AWS、Okta、GitHub、GCP、osquery 等 100+ 数据源的安全 agent，复杂告警处置时间缩短约 70%、值班通知减少 20%，可自行生成草稿 PR。同期 QCon 上海，阿里孙鹏提出 "Read, Don't Write" 的 BoRP 探测式评测，评测成本降低 97%。背景是 9 月 3 日发布的 GPT-6 Astra：105 万 token 上下文、$10/$50 每百万 token，OpenAI 首个达到 Critical 网络安全档位的模型。

─── 【为什么重要】 ───

三条互不相关的报道其实指向同一个结构变化：Agent 的竞争指标已经从"能不能完成任务"转向"无人看管下能持续多久，且错了能不能自己发现"。"检查频率"第一次成了可量化的信任单位。

时机也说明问题。Astra 相对上一代 Sol 定价涨了约 2.5 倍，与两天前的 Claude Fable 5.1 完全对齐；OSWorld 2.0 拿到 72.6%，任务耗时从约 75 分钟压到约 40 分钟。能力在溢出，单价在上升，那么真正能省的资源就只剩一种：人的注意力。低频 check-in 的经济价值不在算力，而在工程师的时间。

反面同样清晰。Wiz 的 GhostApproval 报告指出 6 款 AI 编码助手可被恶意代码库欺骗，向用户展示"看似无害"的审批提示；OpenAI 同期披露过沙箱逃逸；Astra 又被正式标记为 Critical 网络安全档位。信任边界向外推，攻击面同步向外推——这是同一件事的两面。

─── 【架构师解读】 ───

第一，自验证是规模化监督的唯一杠杆。Perplexity 的做法本质是让模型生成测试夹具：把"制造一个可信的失败场景"的边际成本压到接近零。Cognition 让 Devin 测自己，是同一骨架。这意味着接下来 agent 产品的分水岭不是任务成功率，而是"自证能力"——没有自证机制的系统，不配被降低监督频率。

第二，记忆是第二块地基，且与模型强弱无关。Figma 明确列出三类记忆：历史告警、行为指南、习得的数据库结构，并对近期结果加权——两天前的相似告警比半年前的重复告警更有用。这是数据资产的复利，不是参数的复利。把每次人类判断沉淀成可检索资产，比等下一代模型更实际。

第三，低频 check-in 的前提是高频廉价信号。阿里 BoRP 的思路是让模型"读"隐状态而不是"写"评语：用对比表示加 PLS 回归头，8B 模型做到 GPT-4 级评测精度、成本降到约 3%，并在万亿级流量的 A/B 中落地。逻辑链是闭环的——没有便宜的在线体温计，就无法既减少人工检查又及时发现漂移。评测不是质量部门的成本项，它是自动化信任的基础设施。

第四，物理世界在走同一条曲线。亮源新创把 2000+ 互联网真实场景转成仿真，产出 4000+ 小时视觉—语言—动作经验，同一模型零样本迁移到人形、四足、轮式和飞行本体；其结论值得记下：扩大环境覆盖度比在同环境里堆轨迹更能提升泛化。Light REACT 更进一步——部署时抽掉故障标签，只给 64 帧因果上下文的 Transformer，让机器人从自身交互史推断"现在身体是什么状态"，再用偏好强化学习把行为拉回来（直立行为从约 42% 升到约 76%）。这和 Astra 的长上下文、Figma 的记忆层是同一个数学：用上下文替代重训。

第五，需要泼一点冷水。这些案例的场景后果都很低、且可回滚：对外沟通稿、告警分诊、草稿 PR。Perplexity 讲"修改真实系统"，但给出的例子是测试程序。Figma 的护栏是缩小动作范围，PR 默认草稿态；GhostApproval 的教训恰恰是审批提示本身可能被内容伪造——所以审批面必须独立于被审内容，且对模型输出保持不可说服。写操作默认草稿态，不是保守，是当前唯一可靠的工程折中。

商业层面的信号是，OpenAI 在发布 11 天后齐发 Perplexity 与 Cognition 两份落地叙事，售价却与 Fable 5.1 分毫不差。价格战暂时停火，竞争焦点转向监督成本。谁的 agent 能让人少看一眼，谁拿下下一个采购周期。

─── 【对从业者的启示】 ───

1. 把 check-in 频率做成 SLO：例如"每 100 次写操作需要几次人工介入"，与任务成功率并列看板。只看成功率会系统性高估 agent 的可用度。

2. 让模型自己造测试夹具与依赖替身，是当下投入产出比最高的自验证手段。先在 CI 落地，暂不碰生产权限。

3. 建记忆三件套：历史事件、行为准则、系统结构，并做时间衰减。这是极少数会随时间自动增值的资产。

4. 评测降本要敢换范式：能用隐状态读信号的地方就别用生成式 Judge，把昂贵的 Judge 留给有争议样本和上线前把关。

5. 护栏顺序不要颠倒：先精确率、后召回率（Figma 的原话），先缩小动作范围，再谈扩大自治范围。

─── 【参考来源】 ───

📍 来源：[Perplexity trusts GPT-6 Astra with end-to-end systems](https://openai.com/index/perplexity-improving-accuracy-with-astra)
📍 来源：[Cognition helps Devin test its own work with GPT-6 Astra](https://openai.com/index/cognition-devin-testing-with-astra/)
📍 来源：[Figma 如何利用 AI 代理提升安全性](https://www.infoq.cn/article/eS4M9XEPmLbkxksCyAye)
📍 来源：[Read, Don't Write：重塑大模型评价体系](https://www.infoq.cn/article/0kYhxXxhOXhxGATe64ec)
📍 来源：[2000+真实场景搬进仿真：一个导航模型零样本"通吃"四种机器人本体](https://www.qbitai.com/2026/09/488672.html)
📍 来源：[OpenAI Releases GPT-6 Astra: A 1.05M-Context Computer-Use Model](https://marktechpost.com/2026/09/03/openai-releases-gpt-6-astra-a-1-05m-context-computer-use-model-gated-behind-a-critical-cyber-threshold)