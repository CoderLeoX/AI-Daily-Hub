**🔥 一个会话吃掉所有标签页：Anthropic 把路由权交给模型**

─── 【事件速览】 ───

2026 年 9 月 16 日，Anthropic 宣布把 Claude Chat 与 Claude Cowork 合并为「one Claude」单一界面，并把 4 月上线的 Claude Design 从独立产品改为任意对话内可用。同日发布 Claude Docs 与 Claude Slides（beta）：文档支持多人实时协作、Claude 参与起草与评论，可导出 Google Docs / Word；幻灯片可在 Claude 内直接演示或导出 PowerPoint / PDF。官方解释是用户抱怨「要自己判断任务该放哪个标签页」，现在由 Claude 自行判断任务需要什么能力。

节奏：先 Pro / Max（Web、桌面、移动）数周内铺开，Team 与 Free 后续；Docs / Slides / Design 均 beta，需企业管理员显式开启；Claude Code 暂不并入。同一天，Google 开放 Google Home MCP 早期访问（订阅 20 美元/月），NVIDIA 发布 Vera Rubin NVL72 在 MLPerf Inference v6.1 的首秀成绩。

─── 【为什么重要】 ───

重要性不在「多了一个文档工具」，而在于产品线公开承认了一个结构性问题：多产品并存时，任务分类的成本被推给了用户。功能密度到某个临界点后，用户的认知开销会超过功能带来的收益。

架构含义更关键：过去「选标签页」是人在做能力路由，现在路由交给模型。路由权一旦上缴，上下文、Skills、连接器、Artifacts 就必须收敛进同一个生命周期——这是「Agent 平台」与「聊天套壳 + 若干独立 Agent 产品」的分水岭。

商业上，单一入口把 premium 能力捆进一个订阅，把用户时长与上下文锁在一个产品内；企业侧则是把分散的员工 AI 使用收拢到一个可管理的面。同日 Google 反向开放 MCP、NVIDIA 把推理吞吐再抬一档，说明应用层在收敛入口、基础设施层在开放接口并压低每 token 成本——两者互为条件。

─── 【架构师解读】 ───

一、这不是 UI 改版，是把能力路由提到产品默认层。
用户原先要在脑子里维护一张路由表：短问答→Chat，跨文件长任务→Cowork，视觉稿→Design。现在这张表由模型持有。工程上等价于把任务规划、工具选择、执行循环从客户端编排下沉到模型内部。Cowork 本就跑在与 Claude Code 同一套 agentic 引擎上（计划—执行—自查），并进对话等于把那套循环设为默认执行路径。收益是上下文不再跨容器复制与断裂；代价是单次请求的失败面变大——以前 Cowork 挂了不影响 Chat，现在同一会话同时承载对话与长任务。

二、竞争维度从「生成质量」转向「组织级适配」。
Docs / Slides 让 Anthropic 站到了 Google Workspace 与 Microsoft 365 的正面。但这块市场决定去留的从来不是生成得多好，而是格式互操作、模板稳定性、共享权限、管理员控制粒度。导出 Docs / Word / PPTX 是入场券不是护城河。The Verge 的判断成立：模型更强不等于赢，Google 的优势是原生长在文档套件里。Anthropic 现在补的是「少一个离开 Claude 的理由」，还不是「多一个必须用 Claude 的理由」。而这些脏活（权限、审计、模板兼容）的迭代速度远慢于模型，最容易被 beta 期的乐观掩盖。

三、默认自治 + 全量连接器 = 爆炸半径重定义。
一个会话挂着所有 Skills 与连接器，加上「默认动作前确认、可切成连续执行」，意味着 prompt injection 的攻击面从「某一个工具」扩成「整个企业数据面」。Anthropic 的处理有诚意：beta 需管理员开启、默认先问再动、保留人工终审。但这是产品侧护栏，不是工程侧隔离。企业真正需要的是能力级权限分区（哪些连接器不允许出现在同一会话）、按任务可撤销的凭证、以及「模型选了哪条路径」的可观测记录——三者目前都不完整。

四、成本口径会被迫重写。
Chat 的计费直觉是「按 seat + 少量 token」，Agent 的直觉是「按任务时长 × 工具调用 × 上下文重放」。合并后两种消耗混在同一会话里，财务侧无法按旧模型归因。值得注意的反例：OpenAI 同方向推进（ChatGPT + Codex，可能还有 Atlas），而 Claude Code 暂时保持独立。合理解释是开发者面的权限模型、计费口径与审计要求与知识工作面不同，合并收益小于风险。这恰好说明：不是所有面都该合并，产品审美不能凌驾于治理模型。

五、同日的两个对照面。
Google Home MCP 走的是相反路径：把设备与事件历史开放给任何支持 MCP 的 agent（含 Claude、Hermes、OpenClaw），自己退到基础设施层。Google 不赌单一 agent 胜出，它赌所有 agent 都要接它的设备图。Vera Rubin NVL72 在 MLPerf v6.1 首秀给出对 GB300 NVL72 最高 3.7x（Qwen3-VL）/ 2.5x（DeepSeek-R1）的吞吐提升，说明「多步 agent 编排」这种昂贵模式的单位成本仍在下降。应用层收敛入口、协议层开放接口、硬件层压低 token 成本——三件事同日发生不是巧合，是同一阶段的三张面孔。所谓「超级 App」在体验层是减法，在系统层是加法：减去标签页，加上路由、权限、归因三套机制。

─── 【对从业者的启示】 ───

1. 把「能力路由」当产品契约来测。模型自主选工具后，要监控的不再只是回答质量，还有路由准确率与兜底路径，并为其设 SLO。
2. 连接器做最小权限分区。不要让一个会话同时持有生产库、邮件、文件系统三类凭证；爆炸半径要按会话算，不是按账号算。
3. 审计日志记「决策」而非只记「输入输出」。记录每次任务中模型选中的 skill / 工具序列与触发理由，否则事故无法复盘。
4. 重做成本模型。把 seat 计费换成「任务类型 × token × 工具调用」的归因表，否则预算会失控在看不见的长任务上。
5. 选型问三句：路由可解释吗？权限能分区吗？会话成本可分账吗？三个都否，就当聊天工具用，别当平台接。

─── 【参考来源】 ───

📍 *来源：[Claude Cowork and chat are now one Claude（Anthropic 官方）](https://claude.com/blog/cowork-is-now-claude)*
📍 *来源：[Anthropic merges Claude chat and Cowork in one interface（TechCrunch）](https://techcrunch.com/2026/09/16/anthropic-merges-claude-chat-and-cowork-in-one-interface/)*
📍 *来源：[Anthropic to fold Claude AI features into one interface, launches document tools（Reuters）](https://www.reuters.com/business/media-telecom/anthropic-fold-claude-ai-features-into-one-interface-launches-document-tools-2026-09-16/)*
📍 *来源：[Anthropic merges its chat and agentic products into one AI assistant in push to build a superapp（Fortune）](https://fortune.com/2026/09/16/anthropic-merges-its-claude-chat-and-agentic-cowork-products-into-a-single-ai-assistant-as-part-of-a-push-to-build-an-ai-superapp/)*
📍 *来源：[Claude comes for Gemini with its own take on Docs and Slides（The Verge）](https://www.theverge.com/ai-artificial-intelligence/996234/anthropic-one-claude-cowork-docs-slides)*
📍 *来源：[Choosing between Claude Cowork or Chat（Claude 官方文档，agentic 引擎表述）](https://claude.com/resources/tutorials/choosing-between-claude-cowork-or-chat)*
📍 *来源：[Your AI agents can now control your Google Home devices（TechCrunch）](https://techcrunch.com/2026/09/16/your-ai-agents-can-now-control-your-google-home-devices/)*
📍 *来源：[NVIDIA Vera Rubin NVL72 Delivers Leading Performance in MLPerf Inference v6.1 Debut（NVIDIA Blog）](https://blogs.nvidia.com/blog/vera-rubin-nvl72-mlperf-inference/)*