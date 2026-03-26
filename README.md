# opbr-skills

一些 AI Agent **Skills** 合集 —— 让 AI 助手更聪明、更好用。

## 什么是 Skill？

Skill 是一套结构化的指令文件，用于扩展 AI Agent（如 Antigravity、Claude 等）的能力边界。每个 Skill 包含：

- **`SKILL.md`**：核心指令文件，定义触发时机、工作流程和最佳实践
- **`references/`**：参考资料、模板与示例（可选）

只需将 Skill 文件夹放入项目的 `.agents/`、`.agent/`、`_agents/` 或 `_agent/` 目录，AI Agent 即可自动识别并使用。

## Skills 列表

### 📊 [infographic-maker](./skills/infographic-maker/)

> 将原始数据、统计数字、报告文本转化为精美的交互式 HTML 信息图表。

**触发场景：**
- 粘贴 CSV、表格或带数字的数据
- 说"帮我做个图表"、"数据可视化"、"做成信息图"
- 分享报告后希望生成视觉摘要
- 想用漂亮的方式呈现统计数据

**特性：**
- 使用 Chart.js 生成柱状图、折线图、饼图、散点图等
- 输出完全自包含的单个 HTML 文件，无外部依赖
- 支持动画、悬停提示、移动端自适应
- 内置多套专业配色方案

---

### 🎓 [source-code-learner](./skills/source-code-learner/)

> 通过结构化的交互式引导，帮助程序员从零开始理解并重建真实开源项目。

**触发场景：**
- 说"帮我学这个项目"、"带我读这份源码"、"从零开始复现 X"
- 想深入理解某个开源库 / 框架的内部原理
- 希望通过动手重建来掌握架构模式
- 备战面试，需要深入研究某个经典项目

**特性：**
- 分阶段生成可视化学习路线图（Roadmap）
- 每步骤提供"概念讲解 → 编码任务 → 代码评审 → 反馈"完整闭环
- 根据学习者水平（初级 / 中级 / 高级）自动调整任务粒度
- 内置检查点测验与阶段性集成测试
- 支持 GitHub URL、本地文件、粘贴代码等多种输入方式

---

## 使用方式

将需要的 Skill 文件夹复制到你项目的 Agent 目录下：

```
your-project/
└── .agents/
    └── skills/
        ├── infographic-maker/
        │   ├── SKILL.md
        │   └── references/
        └── source-code-learner/
            ├── SKILL.md
            └── references/
```
或者
```
npx skills add opbr/opbr-skills
```

## 许可证

[MIT](./LICENSE)
