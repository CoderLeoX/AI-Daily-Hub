**🔥 Google Home 开放 MCP：设备控制被商品化，历史数据才是护城河**

─── 【事件速览】 ───
9 月 16 日，Google 在 Google Home & Nest 官方博客宣布 Home MCP 进入早期访问（Early Access）。这是一台由谷歌托管的 MCP 服务器，端点 https://home.googleapis.com/mcp，OAuth 作用域为 home.platform.v2，向外部智能体开放五类工具：list_homes（结构发现）、list_home_resources（设备、房间、trait 与命令 schema）、list_home_states（实时状态）、run_home_actions（参数化动作执行）、list_home_history（历史状态与事件日志）。覆盖 Nest 摄像头/门铃/温控与 Works with Google Home、Matter 生态设备。官方点名的客户端包括 Google Antigravity、Claude、Hermes、OpenClaw 与 ChatGPT。门槛同样明确：仅美国英文、仅 Google Home Premium Advanced 订阅（20 美元/月，200 美元/年），用户需自建 Google Cloud 项目、配置外部受众 OAuth 同意屏与 Web 客户端并发布应用。谷歌同时上线面向开发者的 Home Developer MCP（文档与 Matter 规范检索，API key 认证），两者定位分离。安全侧声明为"限流 + 禁止解锁门锁等敏感操作"，熟悉人脸数据另需结构管理员单独授权。Google 强调 Gemini for Home 仍是主入口，MCP 只是新增一层控制。

─── 【为什么重要】 ───
第一，MCP 完成了从"开发者胶水"到"物理世界执行协议"的升格。此前 MCP 的落点是文件、数据库、SaaS API——动作错了重跑一次即可。落到恒温器、门锁、报警**系统**上，动作有物理副作用且不可回滚。标准走进真实世界，工程约束的性质变了。

第二，竞争焦点从设备覆盖转向身份与授权。智能家居过去比"支持多少设备"，现在比"谁能安全地代表你行动"。OAuth 作用域、二级同意、吊销入口、审计可见性——这些原本属于企业 IAM 的词汇，正在进入客厅。谁能把"agent 身份"做成消费者可理解的东西，谁就拿到下一层的入口。

第三，护城河的位置移动了。Matter 已经统一设备层，控制能力被商品化，本地协议（Thread/Zigbee/HA）往往做得比云更好；真正稀缺的是长期事件历史与摄像头语义。谷歌把它锁在 20 美元档、只对美国英文开放，等于用定价和地域当实验控制变量。

第四，站位选择值得注意。谷歌把 Claude、ChatGPT、Hermes、OpenClaw 一起写进支持列表，包括竞争对手。它不打算赢 agent 层，而是选择成为智能家居的基座。The Verge 拿 AWS 作比是准确的。

─── 【架构师解读】 ───
这不是"智能家居多接了几个 AI"，而是一次控制面与推理面的解耦。

看接口就清楚：五个工具里，前四个都是任何 Matter 厂商都能提供的动作层，第五个 list_home_history 才是谷歌真正的资产——跨设备连续事件、摄像头语义摘要、熟悉人脸。"去年谁几点回家""一周洗了几次衣服""客厅灯亮了多久"这类时间序列，只有同时拥有摄像头和云端推理的一方拿得到。所以 MCP 被捆在 Advanced 档不是随手设的付费墙，而是定价锚点的公开声明：卖的是历史和语义，不是开关。

真正的架构动作在授权模型上，谷歌做了分级。一级是标准 OAuth 作用域 home.platform.v2，覆盖结构、设备、状态、历史。二级是熟悉人脸——生物特征衍生数据——走独立的功能同意流：链接形如 home.google.com/connections/feature_consent?client_id=…&structure_id=…&features=1，由结构管理员显式授权，且该结构内至少需有一台启用熟悉人脸检测的 Nest 摄像头或门铃。也就是说，生物特征授权的作用域是（客户端 × 结构）这一对，而非账号级，可逐项撤销。这个模式值得抄：把高敏感数据从粗粒度 token 中拆出来，做成可单独授予、可单独审计、按资源收敛的 secondary consent。

安全侧的问题是原语选择。"禁止解锁门锁这类敏感动作"是动作黑名单，在开放的 Matter 设备分类上不可穷举：门锁能禁，车库门、报警撤防、暖通设定、第三方 Matter 锁呢？更要紧的是，MCP 天然凑齐了"致命三要素"——私有数据（历史 + 摄像头语义）、不可信内容（设备名、厂商云下发元数据、摘要文本）、动作能力，三样在同一个 server 上齐了。不需要有人攻破谷歌：一段被注入的摘要文本，加一个持有 run_home_actions 的 agent，就是一个可被远程说服的执行器。谷歌在文档里自己写"连接后可能出现意外甚至不希望的行为"，这在安全上是相当重的免责声明。正确原语应是与设备类别、动作、时限绑定的能力授权加写操作确认门，而不是全局 denylist。反倒是社区先做对了：开源的 google-home-blade-mcp 已经实现了 GOOGLE_HOME_WRITE_ENABLED 写闸、confirm=true 确认闸与凭证清洗。

配置摩擦是刻意的，也是这版最大的商业瓶颈。用户要自建 GCP 项目、建外部受众同意屏、建 Web 客户端并配置重定向 URI、发布应用——开发者级流程出现在消费级产品上，不是疏忽。OAuth client 是问责与吊销的锚点，也把首波用户过滤成能忍受这套流程的人，灰度因此可控。但它同时说明这还不是产品：真正的消费级形态依赖 MCP 的动态客户端注册（DCR，Antigravity 已支持），否则"任何智能体都能控制你的家"的接入成本是一张云项目表单。

格局上，agent 层会继续薄利化，基座层的议价权上升。Home Assistant 这类自托管方案走相反路径——本地、无订阅、无 scope，代价是拿不到摄像头语义与大模型侧的历史理解。两条路的分界线就一句：你的数据在谁的推理里。

─── 【对从业者的启示】 ───
一、把 agent 接入当作一类新身份纳管。OAuth client ID 是你日后要吊销的对象，上线前登记谁在哪个结构上持有 run_home_actions，换 agent 或人员变动就撤销，别让它躺在 My Accounts 里吃灰。

二、不要让带写权限的 agent 同时消费不可信文本。摄像头摘要、设备名、厂商元数据都算外部输入。写操作必须有人工确认门，或者干脆只开读路径——server 端禁解锁不覆盖其余攻击面。

三、首期只上读路径：历史分析、自定义看板、跨摄像头摘要。早期访问、仅美国英文、限流未公开、无 SLA，暖通、门禁、报警的闭环仍应留在本地或 Matter 直连路径上。

四、用独立的 home structure 做开发测试（谷歌自己也这么建议）。记住熟悉人脸同意是客户端 × 结构级的，测试结构的授权不会污染主结构，这正好给了你安全的试错空间。

五、把注意力放在身份层而非工具层。DCR、按工具/按资源的 scope、MCP 授权规范的进展，才决定这套东西能否走到普通用户手里；工具多几个不改变格局。

─── 【参考来源】 ───
📍 *来源：[TechCrunch](https://techcrunch.com/2026/09/16/your-ai-agents-can-now-control-your-google-home-devices/)*

📍 *来源：[The Verge](https://www.theverge.com/tech/996310/google-home-mcp-integration-agentic-ai-smart-home-price-release-date)*

📍 *来源：[Engadget](https://www.engadget.com/2260280/google-home-is-going-agentic-via-integration-with-the-mcp-standard/)*

📍 *来源：[9to5Google](https://9to5google.com/2026/09/16/google-home-mcp/)*

📍 *来源：[Google Home Developers｜Home MCP 官方文档](https://developers.home.google.com/mcp/home)*

📍 *来源：[Google Home Developers｜MCP Servers 总览](https://developers.home.google.com/mcp)*

📍 *来源：[Unite.AI](https://www.unite.ai/google-opens-home-mcp-early-access-to-ai-agents-for-smart-home-control/)*