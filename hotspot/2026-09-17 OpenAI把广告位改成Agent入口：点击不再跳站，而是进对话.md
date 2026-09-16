**🔥 OpenAI把广告位改成Agent入口：点击不再跳站，而是进对话**

─── 【事件速览】 ───

9月16日（美东），OpenAI 发布 Reimagining advertising with AI，同时动三处。第一，开始在美国与部分广告主测试 Sponsored Agents：用户点击 ChatGPT 内的广告后不再跳转外部站点，而是进入一个明确标注的品牌自有智能体会话，追问、比价、看细节，最后由用户自行点链接去品牌官网。OpenAI 强调这段会话与 ChatGPT 的独立答案分开，也与用户原本的会话相互独立。第二，投放操作搬进对话：广告主用自然语言配 Ads Manager 插件建投放、改预算、看数据，Ads Manager 内加入 AI 创意建议与可选的语境改写、自动翻译。第三，接入 HubSpot（首个 CRM 伙伴）与 Shopify（首个电商伙伴），HubSpot 用户可在其后台直连 ChatGPT Ads 账户建广告、跟线索，美国 Shopify 商家可用 ChatGPT Ads 应用，9月23日扩展到已开放广告的市场。

―――

─── 【为什么重要】 ───

广告诉求的对象变了一次。过去二十年广告技术栈的本质是“把用户送走”：点击、跳站、落地页、像素回传，归因链的最后一段永远发生在别人家的服务器上。Sponsored Agent 把转化动作留在 ChatGPT 内部，广告位第一次同时是入口、容器和测量点。控制点因此整体上移——平台不再只卖曝光和点击，而是定义什么算一次转化、哪些事件能回传给你。

配套的 HubSpot 与 Shopify 集成说明这不是单点格式实验，而是把 CRM、库存与线索回路并进同一个会话界面。商业上也是必然：推理成本高、订阅价与 token 成本长期倒挂，广告与交易抽成是唯一能规模化的第二曲线。这条线只跑了七个月——2月美国小范围测试，4月转 CPC，8月上线商品轮播、扩到31个欧洲市场，8月底年化收入 10 亿美元，9月11日 Amazon 的广告主也开始能在 ChatGPT 买广告。Google 的文本链、Meta 的信息流、TikTok 的竖屏都定义过各自的时代，OpenAI 正在找它自己那一个。

―――

─── 【架构师解读】 ───

一、难的不是 agent，是隔离。OpenAI 那句“会话与独立答案分开、与原会话相互独立”翻译成架构语言就是：需要一个会话级信任域——品牌可配置的 system prompt、受限工具集（目录、库存、订单、工单）、独立记忆与状态、独立输出审查与审计日志，且不得污染主会话上下文与用户画像。多租户隔离、上下文串味、越权话术、报价与库存幻觉，一旦出事责任在品牌方还是平台？这是这套方案里第一个真实的合同与合规问题，比模型跑分重要得多。

二、广告主的资产被重新定义。过去核心资产是站内转化率和第一方数据；现在要准备的是“能被对话消费”的商品与客户数据——结构化、可被 agent 调用的 inventory/CRM 字段，以及一个不乱说话、能被客服和销售接管的品牌 agent。Shopify Catalog 直连就是这个逻辑：谁的数据模型更接近机器可读，谁的渠道接入成本更低。

三、测量权是新的议价点。截至目前，OpenAI 没有公布参与广告主名单、测试规模、定价与转化数据，agent 的技术边界也未说明。Digiday 的观察是广告主普遍认为“有前景，但 ROI 还没到”，预算仍在实验池里。这是格式验证阶段，不是效果验证阶段。更关键的是，会话内转化天然缺少跨平台 correlation id：哪个 session 对应哪次成交、能否回传进 CRM，目前平台说了算。架构上不要把关键转化事件的唯一事实源放在平台侧。

四、投放界面迁移会改变工程师的工作方式。自然语言建 campaign 成立，意味着对话成了广告运营的控制面。对技术团队的含义是：营销与 CRM 系统必须有确定性的 API 或 MCP 接口，否则只能靠人肉 prompt 操作，既不可审计也不可复现。

五、中立性成本最终由用户承担。广告与答案共用一个界面，信任是最脆弱的资产。强隔离、明确标注、只在美国小范围测试，本质是把“可商业化域”与“可信域”分开治理。这个边界一旦模糊——比如广告方按你的对话意图动态定价——监管就会进来，欧洲 DSA 已经在盯这件事。

综合判断：方向值得押注，但押的是可迁移能力，不是这个平台。会话内转化加 agent 渠道，大概率会在 12 个月内成为标配形态；但此刻的平台数据、测量口径与责任边界都不足以支撑架构级绑定。7个月 10 亿美元年化证明需求真实（据 Digiday 早前报道，CPM 约 60 美元、部分广告主要求 20 万美元起投，与流媒体和高端电视同档，说明它卖的是高意图上下文而不是流量），但“卖姿势”和“卖结果”是两门生意。

―――

─── 【对从业者的启示】 ───

1. 别追广告格式，先建隔离层。多租户会话隔离、品牌侧上下文边界、越权输出拦截、可审计日志，这些组件在广告、客服、销售场景里复用率最高，今年做不会白做。

2. 把商品与客户数据做成机器可读资产。SKU、库存、价格、服务条款要能被 agent 确定性调用，而不是仅为人看的网页。这是接入任何 agent 渠道的前置条件。

3. 归因与观测自己留一手。会话级 correlation id、关键转化的自有埋点、平台侧数据的对账机制，都要在接入前设计好，别等出事再补。

4. 用可迁移能力选型。评估渠道时问三个问题：数据能否导出、责任如何划分、测量口径是否透明。答案为否就先小预算试，不进主预算。

5. 盯两个信号做判断。9月23日的国际扩展是否同步开放 agent 格式，以及 Amazon Ads 的 pilot 是否升级为常态通道。两者同时成立，才算产业转向。

―――

─── 【参考来源】 ───

📍 *来源：[OpenAI Blog：Reimagining advertising with AI](https://openai.com/index/reimagining-advertising-with-ai)*
📍 *来源：[Digiday：OpenAI's next ChatGPT ad format — click to chat, not to site](https://digiday.com/marketing/openais-next-chatgpt-ad-format-click-to-chat-not-to-site/)*
📍 *来源：[The Next Web：OpenAI tests Sponsored Agents in ChatGPT](https://thenextweb.com/news/openai-chatgpt-sponsored-agents-ads-manager-hubspot-shopify)*
📍 *来源：[Digiday：ChatGPT enters the ad game. Now what?](https://digiday.com/podcasts/chatgpt-enters-the-ad-game-now-what)*
📍 *来源：[Reuters：OpenAI tests advertiser-sponsored agents](https://www.reuters.com/technology/)*

注：公众号发布通道仍为停用状态（mp_publish=false），以上是成稿文本，可直接复制使用；如需恢复发布再单独确认。