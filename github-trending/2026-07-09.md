**GitHub Trending 每日精选 | 2026.07.09**

• 核心主线：AI Agent 工程技能与基础设施项目集中爆发，涵盖生产级技能框架、本地记忆方案、空间感知与文档自动化。

─── 【AI Agent 技能与框架】 ───
1️⃣ agent-skills
AI 编码 Agent 的生产级工程技能合集，提供经过实战验证的 prompt 与 skill 模版，可直接集成到 Cline、Codex 等 Agent 中。工程影响：缩短 Agent 行为定制从周到小时。
📍 *来源：[agent-skills](https://github.com/addyosmani/agent-skills)*

2️⃣ superpowers
一套 Agent 技能框架与软件开发方法论，强调可复用的 skill 组件与结构化协作流程。工程影响：为多 Agent 协作提供统一规范层。
📍 *来源：[superpowers](https://github.com/obra/superpowers)*

3️⃣ last30days-skill
一个 AI Agent 技能，可跨 Reddit、X、YouTube、HN、Polymarket 及 web 搜索任意主题，并综合给出有溯源的时间窗口总结。工程影响：时效性情报聚合的 Agent 化标杆。
📍 *来源：[last30days-skill](https://github.com/mvanhorn/last30days-skill)*

─── 【AI 基础设施与数据】 ───
4️⃣ TencentDB-Agent-Memory
腾讯云开源的 Agent 长期记忆方案，通过四层渐进式 pipeline 实现全本地存储，零外部 API 依赖。核心：用 Agent Memory 替代 RAG，降低推理成本与延迟。工程影响：可直接作为 Agent 记忆层的后端替换。
📍 *来源：[TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)*

5️⃣ zvec
阿里巴巴出品的轻量级进程内向量数据库，极速、低消耗。定位：替代 Milvus/Chroma 在嵌入式或边缘场景的部署痛点。工程影响：内存与延迟敏感场景的最佳选择。
📍 *来源：[zvec](https://github.com/alibaba/zvec)*

(0709 0631 P1/3)

─── 【开发与运维工具】 ───
6️⃣ prisma
新一代 Node.js/TypeScript ORM，支持 PostgreSQL、MySQL、MongoDB 等主流数据库，提供类型安全的数据访问层。工程影响：全栈项目的 ORM 首选，持续活跃更新。
📍 *来源：[prisma](https://github.com/prisma/prisma)*

7️⃣ argo-cd
Kubernetes 声明式持续部署工具，GitOps 的事实标准。工程影响：K8s 运维栈中自动同步与回滚的核心组件。
📍 *来源：[argo-cd](https://github.com/argoproj/argo-cd)*

8️⃣ OfficeCLI
首个专为 AI Agent 设计的 Office 套件 CLI，支持读写编辑 Word、Excel、PowerPoint，单二进制无 Office 依赖。工程影响：Agent 自动化文档处理的关键工具，填补 Agent 直接操作 Office 文件的空白。
📍 *来源：[OfficeCLI](https://github.com/iOfficeAI/OfficeCLI)*

─── 【前沿探索与安全】 ───
9️⃣ RuView
将普通 WiFi 信号转化为实时空间智能，实现人体存在检测与生命体征监测，不依赖任何摄像头。工程影响：隐私保护的智能感知技术，适用于智能家居与养老监护。
📍 *来源：[RuView](https://github.com/ruvnet/RuView)*

🔟 system_prompts_leaks
提取并公开了 Anthropic、OpenAI、Google 最新模型的系统提示词，包括 Claude Fable 5、GPT 5.5 Instant、Gemini 3.5 Flash 等。工程影响：逆向工程揭示大模型系统行为的关键资料，对 Agent 开发调优有直接参考价值。
📍 *来源：[system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)*

(0709 0631 P2/3)

─── 【架构师判断】 ───
- 今日 Trending 由 AI / Agent 主导（6/10 个项目），方向高度集中。
- AI 原生应用（agent-skills、TencentDB-Agent-Memory 等）仍在贡献新工具和开发范式，值得跟进评估。

(0709 0631 P3/3)