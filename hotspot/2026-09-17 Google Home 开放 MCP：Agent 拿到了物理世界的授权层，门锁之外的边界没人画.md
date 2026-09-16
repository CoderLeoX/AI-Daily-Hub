**🔥 Google Home 开放 MCP：Agent 拿到了物理世界的授权层，门锁之外的边界没人画**

─── 【事件速览】 ───
2026 年 9 月 16 日，Google 通过 Home & Nest 社区博客（Group PM Taylor Lehman 署名）开放 Home MCP 早期访问。这个 MCP Server 暴露五个工具：list_homes（枚举住宅与结构）、list_home_resources（房间、设备、trait 与命令 schema）、list_home_states（实时连接与 trait 状态）、run_home_actions（执行参数化控制命令）、list_home_history（按时间范围查历史状态与事件日志）。覆盖 Nest 摄像头、门铃、温控器，以及 Works with Google Home / Matter 设备。官方点名 Antigravity、Claude Cowork、OpenClaw、Hermes 等任意支持 MCP 的客户端。服务地址 home.googleapis.com/mcp，OAuth scope 为 home.platform.v2，SSE 传输。门槛不低：需 Google Home Premium Advanced 订阅（20 美元/月）、美国英语区、自建 GCP 项目并申请审批、启用 Home API、配置 OAuth 同意屏幕与重定向 URI。安全侧声明限流并禁止解锁门锁等敏感动作，熟悉面孔数据另需结构管理者单独授权。已知限制：自动化创建暂不支持，部分 trait 标记为实验性，官方承认延迟偏高。

─── 【为什么重要】 ───
MCP 此前的主战场是开发者的工具链：找文档、调 API、跑 notebook。这次不一样——协议被抬到了物理世界的控制平面上。门锁、温控、摄像头事件历史，这些是会发热、会开门、会录像的权限对象，而 Google 把它交给了第三方 Agent。真正值得研究的不是"能做什么"，而是 Google 给出的三件东西：一个粗粒度 scope、一份服务端动作黑名单、一层限流。这是首个消费级平台对"Agent 直控物理设备"的公开答卷，好与坏都会被行业照抄。理解它的取舍在哪、缺口在哪，比讨论它能省几次手动开关重要得多。

─── 【架构师解读】 ───
第一，权限粒度错配是结构性缺陷。home.platform.v2 一个 scope 同时打包了枚举、实时状态、设备控制、历史事件四类能力。我只想做一个灯光场景 Agent，也必须一并拿到跨房间摄像头事件历史与录像摘要的读权限。有意思的是 Google 自己在熟悉面孔数据上加了独立同意流程——这恰恰证明通用的 scope 粒度不够用，是被单个高敏感数据源逼出来的补丁，而不是体系化设计。更值得注意的是风险排序反了：门锁是显性、一次性、可见的；长尾风险来自不可逆的副作用动作（暖通、家电、门禁联动）以及持续性的隐私读。禁令只列了门锁，这是黑名单不是白名单。

第二，"模型不是安全边界"这一点 Google 做对了，但做得还不够。把禁止解锁实现在服务端 tool surface，是最正确的取舍——prompt injection 不可能绕过它。可固定黑名单无法表达"我在家且输入 PIN 时才允许解锁"。平台底层的能力其实更细：Matter / SDM 的 LockUnlock trait 本身就带 remoteSetDisabled 这类控制位。能力存在于设备层，却没有暴露到 Agent 授权层，中间缺的是一个策略引擎：按设备、按动作、按时段、按在家状态、按可逆性分级裁决。可以预期这就是下一版要补的洞。

第三，消费者功能套着开发者外壳，暴露了身份模型的空缺。让普通用户自建 GCP 项目、配同意屏幕、发布应用才能把家里灯交给 Agent，说明面向消费者的 Agent 授权管理还没建出来，只能借用 Cloud 的机器。后果很实在：授权与撤销以"用户 OAuth client"为单位，Agent 的动作全部归因到用户本人。而 Google 自己的 Cloud MCP 文档明确建议生产环境使用独立的 agent / workload identity。消费场景里 agent 与 user 被混为一谈，一旦出事故，取证和按 Agent 粒度止损都会卡住。

第四，风险分期是合理的，可观测性却留了空白。刻意不支持"创建自动化"，先开读、再开控、最后才谈持续自主运行，这是教科书式的风险分期；限流则是策略缺位时对爆炸半径的兜底。但文档没说清两件事：Agent 动作的完整审计日志由谁提供，用户在哪里能看到"它刚才动了什么"。如果只有设备事件历史、没有 Agent 归因，误动作发生时排障无从下手。

第五，生态层面 Google 在做对冲。用订阅制把"物理上下文"变现，把 Home 变成任何 LLM 都能挂载的感知与执行外设——不赌自家助手赢，赌自己是那一层。对没有硬件的 Agent 厂商，这是免费拿到真实世界执行器的入口。同时 Google 还发布了第二个 Home Developer MCP，面向编码工具做文档 grounding，认证走 API key 而非用户 OAuth。同一家公司、同一协议、两套认证模型，说明 MCP 的认证体系远未成熟，谁先补上企业级 Agent 身份标准，谁就定规则。

─── 【对从业者的启示】 ───
1. 别抄黑名单，建策略面。把禁止项从硬编码改成默认拒绝的策略：按设备、动作、时段、人在不在家、可逆性分级，不可逆动作强制二次确认。黑名单永远追不上设备类型增长。
2. 工具返回值全部视为不可信输入。摄像头事件摘要、设备名、历史日志都是可被外部影响的字符串，正是间接 prompt injection 的载荷通道。读通道与写决策通道必须分离，写操作要走结构化校验过的意图对象。
3. 用独立身份跑 Agent，别复用用户身份。动作归因必须能区分"Agent 做的"和"我做的"，否则无法取证、无法按 Agent 粒度撤销。这是 Google 自己的 Cloud MCP 文档给出的建议。
4. 自建一层 Agent 权限网关。假定上游 scope 长期粗粒度，把策略、审计、限流、熔断放在你可控的代理层，平台换代时不必重写业务逻辑。
5. 只读先行，先量延迟。官方已承认延迟偏高，涉及温控、安防联动的闭环控制前，先测 P95 往返与重试代价，别把时序敏感逻辑交给不可控的第三方控制平面。

─── 【参考来源】 ───
📍 *来源：[Google Home MCP Server 官方文档](https://developers.home.google.com/mcp/home)*
📍 *来源：[Home MCPs 总览（Google Home Developers）](https://developers.home.google.com/mcp)*
📍 *来源：[Introducing Home MCP（Google Home & Nest 社区博客）](https://support.google.com/googlehome/blog/467705013/introducing-home-mcp-enabling-your-agent-to-interact-with-your-home)*
📍 *来源：[Your AI agents can now control your Google Home devices（TechCrunch）](https://techcrunch.com/2026/09/16/your-ai-agents-can-now-control-your-google-home-devices/)*
📍 *来源：[Google Home gets MCP support for third-party AI agents（The Verge）](https://www.theverge.com/tech/996310/google-home-mcp-integration-agentic-ai-smart-home-price-release-date)*
📍 *来源：[Google Opens Home MCP Early Access（Unite.AI）](https://www.unite.ai/google-opens-home-mcp-early-access-to-ai-agents-for-smart-home-control/)*