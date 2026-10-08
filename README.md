# IT爱学堂-Agent Skills 多平台应用实战「完结无密」
获课：aixuetang.xyz/24483/

拆解技能系统——SKILL.md 规范与渐进式披露的技术本质
Agent Skills 不是提示词的简单封装，而是一套拥有独立规范的技术标准。理解这套标准的内在结构，是跨平台部署的第一道门槛。

从提示到技能：知识封装方式的根本转变
传统 Prompt 是一次性对话指令，用完即弃。Agent Skills 将领域经验封装为可复用、可版本化的能力包，以 SKILL.md 文件为载体，包含 YAML frontmatter 元数据和 Markdown 正文指令。2025 年 10 月 Anthropic 首次推出这一概念，同年 12 月 18 日正式开源为跨平台标准，规范编号 Agent Skills Specification V1.0，托管于 agentskills.io，同步发布 Python、TypeScript 和 Java 三套官方 SDK。

截至 2026 年 2 月，公开可用的 Skill 已超过 85,000 个，支持该标准的主流平台达 27 家，涵盖开发、设计、办公、电商、金融等领域。技能正成为智能体生态的基础设施。

SKILL.md 的规范结构
一个 Skill 是一个目录，核心是 SKILL.md 文件，可附带 scripts/、references/、assets/ 等子目录。SKILL.md 分为两个部分：YAML frontmatter 包含 name 和 description 两个必填字段——name 最多 64 字符，只允许小写字母、数字和连字符，且必须与父目录名一致；description 最多 1024 字符，需同时说明技能做什么以及何时使用。可选字段包括 license、compatibility、metadata 和 allowed-tools。

正文部分是实际交给模型的程序性知识，包括工作流程、最佳实践和操作指导。复杂技能可在 scripts/ 目录中附带可执行的 Python、Bash 或 JavaScript 脚本，在 references/ 中存放按需查阅的文档资料。

渐进式披露：为什么技能装再多也不爆上下文
渐进式披露是 Agent Skills 最核心的工程创新。加载分为三级：第一级是元数据，智能体启动时仅将所有技能的 name 和 description 预载进系统提示，每个技能只占几十到一百来个 token；第二级是 SKILL.md 正文，仅当模型判断当前任务与某个技能的 description 匹配时才加载；第三级是附加文件，由模型根据正文指引决定是否进一步读取参考资料或执行脚本。

这一机制带来了三个关键优势：Token 效率——只有需要时才消耗上下文；轻量实现——技能本质上是一组 Markdown 文件，无需额外基础设施即可分发；资源打包——技能可以携带自己的脚本和模板，确保智能体拥有完成任务的精确工具。

理解这套规范是跨平台部署的前提。只有深刻掌握 SKILL.md 的结构约束和渐进式披露的加载逻辑，才能确保技能在不同平台上行为一致。
