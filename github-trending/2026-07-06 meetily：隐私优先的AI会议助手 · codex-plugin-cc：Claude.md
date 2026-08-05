**GitHub Trending 每日精选 | 2026.07.06**

• 核心主线：AI/Agent 工具链全面爆发，开发者工具与安全工具同步推进，嵌入式/边缘学习资源有亮点。

─── 【AI 与工程基建】 ───

1️⃣ meetily：隐私优先的AI会议助手
基于 Rust 构建，100% 本地处理，4 倍速 Parakeet/Whisper 实时转录、说话人分离、Ollama 摘要。无需云服务，适合安全敏感的团队集成。
📍 *来源：[Zackriya-Solutions/meetily](https://github.com/Zackriya-Solutions/meetily)*

2️⃣ codex-plugin-cc：Claude Code + Codex 代码审核插件
允许在 Claude Code 中直接调用 OpenAI Codex 进行代码审查或任务委派，打通两大 AI 编码生态。
📍 *来源：[openai/codex-plugin-cc](https://github.com/openai/codex-plugin-cc)*

3️⃣ system_prompts_leaks：主流模型系统提示词泄露合集
收录 Anthropic（Claude Fable 5、Opus 4.8）、OpenAI（ChatGPT 5.5 Thinking、GPT 5.5 Instant）、Google（Gemini 3.5 Flash、3.1 Pro）等最新模型的系统提示，对逆向工程和 Agent 设计有直接参考价值。
📍 *来源：[asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)*

4️⃣ taste-skill：给 AI 注入“品味”
通过技能层抑制 AI 生成千篇一律的 slop，提升输出多样性。工程上可作为 Claude Code / Codex 的 skill 集成。
📍 *来源：[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)*

5️⃣ claude-skills：337 条技能包集合
涵盖 30+ Agents、70+ 自定义命令、330+ skills，支持 Claude Code、Codex、Gemini CLI、Cursor 等 8 款编码 Agent。开箱即用的技能市场。
📍 *来源：[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)*

6️⃣ romm：自托管 ROM 管理与模拟器
美观、全功能的自托管游戏 ROM 管理器与模拟器，适合嵌入式/游戏主机场景。
📍 *来源：[rommapp/romm](https://github.com/rommapp/romm)*

7️⃣ herdr：终端 Agent 多路复用器
终端内运行的 Agent 多路复用工具，让多个 AI Agent 协作文本交互，类似 tmux 但对齐 Agent 会话。
📍 *来源：[ogulcancelik/herdr](https://github.com/ogulcancelik/herdr)*

(0706 0631 P1/2)

8️⃣ page-agent：自然语言控制网页 GUI Agent
阿里巴巴开源，纯 JavaScript 实现在页面内操作 GUI，支持自然语言指令。适合端侧(浏览器) Agent 自动化。
📍 *来源：[alibaba/page-agent](https://github.com/alibaba/page-agent)*

9️⃣ cs249r_book：哈佛边缘计算 ML 系统教材
《Machine Learning Systems》完整教材，覆盖 ML 系统设计、推理优化、边缘部署。对 ARM 平台选型有直接工程参考。
📍 *来源：[harvard-edge/cs249r_book](https://github.com/harvard-edge/cs249r_book)*

🔟 strix：开源 AI 渗透测试工具
自动化发现和修复应用漏洞，基于 AI 驱动。适合安全运维团队集成到 CI/CD Pipeline。
📍 *来源：[usestrix/strix](https://github.com/usestrix/strix)*

─── 【架构师判断】 ───
- 今日 Trending 由 AI / Agent 主导（8/10 个项目），方向高度集中。
- 嵌入式/边缘计算方向有 1 个项目（cs249r_book），对 ARM 平台选型有参考价值。
- AI 原生应用（meetily、codex-plugin-cc 等）仍在贡献新工具和开发范式，值得跟进评估。

(0706 0631 P2/2)