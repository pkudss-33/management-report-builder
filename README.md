# Management Report Builder

> 一个 Claude Code 技能：将战略思考转化为**单页线性管理报告**（One-Page Linear Report）。

![Skill](https://img.shields.io/badge/Skill-Management%20Report-2457d6?style=flat-square)
![Claude Code](https://img.shields.io/badge/Claude%20Code-Supported-6B5B95?style=flat-square)
![License](https://img.shields.io/github/license/pkudss-33/management-report-builder?style=flat-square)

当你需要快速生成一份**管理层摘要、一页纸报告、核心策略文档**时，告诉 Claude Code，它会自动调用这个技能，输出一份干净、现代、可扫描的单页 HTML 报告。

## 效果预览

干净的企业级设计系统：极细现代无衬线字体（Inter + Noto Sans SC）、冷调配色、网格卡片布局、线性滚动单页。

## 快速安装

### 方式一：git clone（通用，零依赖）

复制下面这行，在终端中运行：

```bash
mkdir -p ~/.claude/skills && git clone https://github.com/pkudss-33/management-report-builder.git ~/.claude/skills/management-report-builder
```

### 方式二：gh skill install（需要 GitHub CLI ≥ v2.90）

```bash
gh skill install pkudss-33/management-report-builder management-report-builder --agent claude-code --scope user
```

### 方式三：npx skills（通用）

```bash
npx skills add pkudss-33/management-report-builder
```

安装完成后，重启 Claude Code 或在新对话中直接使用即可。

## 触发方式

在 Claude Code 中，用自然语言提及以下任一关键词即可自动触发：

| 中文触发词 | 英文触发词 |
|---|---|
| 管理摘要、一页纸摘要 | one page, one-pager |
| 核心策略报告、管理报告 | management report, strategy report |
| 帮我写个一页纸 | executive summary, board briefing |
| 整理成管理报告、做个核心策略摘要 | strategy memo |

**示例对话：**

> "帮我把最近的会议纪要整理成一页纸管理摘要"

> "Generate a one-page strategy report from these Q3 results"

> "把这些战略方向写成核心策略报告"

## 文件结构

```
management-report-builder/
├── SKILL.md                          # 技能定义（触发词、工作流、组件目录）
├── README.md                         # 本文件
├── references/
│   └── methodology.md                # 写作方法论（摄入→提炼→架构→构建→迭代）
└── assets/
    └── one-page-linear-template.html # 完整设计系统模板（20+ 组件，[[...]] 占位符）
```

## 模板组件一览

| 组件 | CSS class | 适用场景 |
|---|---|---|
| Hero 头部 | `.hero` | 报告标题、标签、一句话导语 |
| 章节头部 | `.section-head` + `.section-kicker` | 带编号和标签的章节标题 |
| 双列卡片 | `.two-col` > `.card` | 对比、两种视角 |
| 三列卡片 | `.three-col` > `.card` | 三个支柱/选项/发现 |
| 时间线 | `.timeline` > `.stage` | 阶段性演进、路线图 |
| 公式行 | `.formula` | A + B + C = … 的分解 |
| 表格 | `.table-wrap` > `table` | 结构化维度对比 |
| 逻辑条 | `.logic-strip` > `.logic-card` | 两个概念用箭头/运算符连接 |
| 路径地图 | `.path-map` > `.path-panel` | 双轨流程、决策路径 |
| 角色地图 | `.role-map` > `.role-card` | 组织角色、职责分配 |
| 决策模型 | `.decision-model` > `.model-card` | 两种方案对比（含图） |
| 语音网格 | `.voice-grid` > `.voice-card` | 多个视角/声部 |
| 挑战网格 | `.challenge-grid` > `.challenge-card` | 问题、风险、挑战 |
| 警示网格 | `.avoid-grid` > `.avoid-item` | 反模式、雷区 |
| 流程条 | `.flow` | 横向流程步骤（6列） |
| Callout | `.callout` | 关键判断高亮 |
| Panel | `.panel` | 内联边框内容框 |
| Summary Box | `.summary-box` + `.summary-grid` | 最终总结 |
| One-Page Tabs | `.onepage-tabs` + `.onepage-stage` | 嵌入多个项目子页 |
| 进度条 | `.progress` | 阅读进度指示 |
| 标签 | `.tags` > `span` | 路径步骤上的紧凑标签 |

## 换肤

只需修改 `:root` 中的 CSS 变量即可适配品牌色：

```css
:root {
  --blue: #你的品牌蓝;
  --green: #你的品牌绿;
  --ink: #你的主文字色;
  --wash: #你的页面底色;
  /* ... */
}
```

## 许可证

MIT
