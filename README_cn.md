<div align="center">
    <img src="./media/logo_small.webp"/>
    <h1>🌱 Spec Kit</h1>
    <h3><em>让高质量软件开发更高效。</em></h3>
</div>

<p align="center">
    <strong>通过规范驱动开发（Spec-Driven Development），帮助组织专注于产品场景本身，而非重复造轮子的代码编写。</strong>
</p>

[![Release](https://github.com/github/spec-kit/actions/workflows/release.yml/badge.svg)](https://github.com/github/spec-kit/actions/workflows/release.yml)

---

## 目录

- [🤔 什么是规范驱动开发？](#-what-is-spec-driven-development)
- [⚡ 快速上手](#-get-started)
- [📚 核心理念](#-core-philosophy)
- [🌟 开发阶段](#-development-phases)
- [🎯 实验目标](#-experimental-goals)
- [🔧 前置条件](#-prerequisites)
- [📖 深入了解](#-learn-more)
- [📋 详细流程](#-detailed-process)
- [🔍 故障排查](#-troubleshooting)
- [👥 维护者](#-maintainers)
- [💬 支持](#-support)
- [🙏 鸣谢](#-acknowledgements)
- [📄 许可证](#-license)

## 🤔 什么是规范驱动开发？

规范驱动开发（Spec-Driven Development）**彻底颠覆**了传统软件开发模式。过去几十年，代码一直是主角，规范文档只是辅助，写完代码就被抛诸脑后。而规范驱动开发则反其道而行之：**规范本身可执行**，不仅仅是指导开发，更能直接生成可用的实现。

## ⚡ 快速上手

### 1. 安装 Specify

根据你所用的智能代理初始化项目：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME>
```

### 2. 编写规范

使用 `/specify` 命令描述你想要构建的内容。只需关注**做什么**和**为什么做**，无需关心技术细节。

```bash
/specify 构建一个可以帮助我将照片整理到不同相册的应用。相册按日期分组，并可在主页通过拖拽重新排序。相册之间不嵌套。每个相册内，照片以平铺方式预览。
```

### 3. 制定技术实现方案

用 `/plan` 命令说明你的技术栈和架构选择。

```bash
/plan 应用使用 Vite，尽量少用第三方库。尽可能采用原生 HTML、CSS 和 JavaScript。图片不上传，元数据存储在本地 SQLite 数据库。
```

### 4. 拆解并实现

用 `/tasks` 生成可执行的任务清单，然后让你的智能代理逐步实现功能。

详细分步指南请参见我们的[完整教程](./spec-driven.md)。

## 📚 核心理念

规范驱动开发是一套结构化流程，强调：

- **意图驱动**，先定义“做什么”，再考虑“怎么做”
- **高质量规范**，通过规则和组织原则保障规范质量
- **多步细化**，不是一次性生成代码，而是逐步完善
- **深度依赖**先进 AI 模型对规范的理解与解释能力

## 🌟 开发阶段

| 阶段 | 重点 | 主要活动 |
|------|------|----------|
| **0到1开发**（“绿地”） | 从零开始 | <ul><li>梳理高层需求</li><li>生成规范</li><li>制定实现计划</li><li>构建生产级应用</li></ul> |
| **创意探索** | 并行实现 | <ul><li>探索多种解决方案</li><li>支持多种技术栈与架构</li><li>尝试不同的用户体验模式</li></ul> |
| **迭代增强**（“棕地”） | 旧系统现代化 | <ul><li>逐步添加新功能</li><li>改造遗留系统</li><li>优化开发流程</li></ul> |

## 🎯 实验目标

我们的研究与实验聚焦于：

### 技术中立

- 用多种技术栈构建应用
- 验证规范驱动开发是一种与具体技术、编程语言、框架无关的通用流程

### 企业级约束

- 展示关键任务级应用的开发流程
- 融合企业实际约束（如云服务商、技术栈、工程规范）
- 支持企业级设计系统与合规要求

### 以用户为中心的开发

- 针对不同用户群体和偏好构建应用
- 兼容多种开发方式（从“灵感编程”到AI原生开发）

### 创意与迭代流程

- 验证并行实现探索的可行性
- 提供完善的迭代式功能开发流程
- 支持升级与现代化改造等流程拓展

## 🔧 前置条件

- **Linux/macOS**（或Windows下的WSL2）
- AI编程助手：[Claude Code](https://www.anthropic.com/claude-code)、[GitHub Copilot](https://code.visualstudio.com/)、或[Gemini CLI](https://github.com/google-gemini/gemini-cli)
- 包管理工具：[uv](https://docs.astral.sh/uv/)
- [Python 3.11及以上版本](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

## 📖 深入了解

- **[完整的规范驱动开发方法论](./spec-driven.md)** —— 全流程深度解析
- **[详细操作指引](#detailed-process)** —— 步步详解实施流程

---

## 📋 详细流程

<details>
<summary>点击展开详细的分步操作指南</summary>

你可以使用Specify CLI快速初始化项目，这会自动拉取所需的开发资源。执行：

```bash
specify init <project_name>
```

或者在当前目录下初始化：

```bash
specify init --here
```

![Specify CLI在终端中初始化新项目](./media/specify_cli.gif)

系统会提示你选择所用的AI助手。你也可以直接在命令行中指定：

```bash
specify init <project_name> --ai claude
specify init <project_name> --ai gemini
specify init <project_name> --ai copilot
# 或者在当前目录下：
specify init --here --ai claude
```

CLI会自动检测你是否已安装Claude Code或Gemini CLI。如果未安装，或者你只想获取模板而不检测工具，可加上`--ignore-agent-tools`参数：

```bash
specify init <project_name> --ai claude --ignore-agent-tools
```

### **第一步：** 初始化项目

进入项目文件夹，启动你的AI助手。本例以`claude`为例。

![初始化Claude Code开发环境](./media/bootstrap-claude-code.gif)

当你看到`/specify`、`/plan`和`/tasks`等命令可用时，说明环境配置无误。

第一步建议先生成项目脚手架。使用`/specify`命令，并详细描述你要开发的项目需求。

>[!IMPORTANT]
>请尽可能明确你要做“什么”以及“为什么要做”。**此时无需关注具体技术栈。**

示例提示语：

开发Taskify，一个面向团队的效率提升平台。平台应支持用户创建项目、添加团队成员、分配任务、评论任务，并以看板（Kanban）方式在不同任务板之间移动任务。在本阶段，这一功能称为“创建Taskify”。用户为预设的五人，分为两类：一名产品经理和四名工程师。请创建三个不同的示例项目。任务状态采用标准看板流程，包括“待办”、“进行中”、“评审中”和“已完成”四个列。

本应用无需登录，仅用于最初的功能测试，确保基础功能可用。在任务卡片的界面上，用户可以随时更改任务当前状态，将其在看板的不同列之间移动。每个任务卡片下，用户可以无限次发表评论。用户还可以直接在任务卡片上为任务分配指定的有效用户。

首次启动Taskify时，系统会展示五位用户供选择，无需密码。点击某个用户后，进入主界面，显示所有项目列表。点击项目后，打开该项目的看板页面，展示各个状态列。用户可以通过拖拽方式在不同列之间移动任务卡片。分配给当前登录用户的任务卡片会以不同颜色显示，方便快速识别。用户可以编辑或删除自己发表的评论，但无法修改或删除他人评论。

---

在输入上述需求后，Claude Code会自动启动规划和规范草拟流程，并触发内置脚本以初始化代码仓库。

完成此步骤后，将会新建一个分支（如 `001-create-taskify`），并在 `specs/001-create-taskify` 目录下生成一份新规范文档。

生成的规范文档将包含一组用户故事和功能需求，格式遵循模板。

此时，项目文件夹结构应如下所示：

```text
├── memory
│	 ├── constitution.md
│	 └── constitution_update_checklist.md
├── scripts
│	 ├── check-task-prerequisites.sh
│	 ├── common.sh
│	 ├── create-new-feature.sh
│	 ├── get-feature-paths.sh
│	 ├── setup-plan.sh
│	 └── update-claude-md.sh
├── specs
│	 └── 001-create-taskify
│	     └── spec.md
└── templates
    ├── CLAUDE-template.md
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

### **第二步：功能规范澄清**

在完成基础规范制定后，你可以进一步澄清那些在首次尝试时未被准确捕捉的需求。例如，你可以在同一个Claude Code会话中使用如下提示：

```text
每个示例项目或你创建的项目都应包含5到15个任务，任务数量不固定，且这些任务应随机分布在不同的完成阶段。请确保每个阶段至少有一个任务。
```

你还应让Claude Code对**评审与验收清单**进行校验，勾选那些已通过或符合要求的条目，未通过的则留空。可以用如下提示：

```text
阅读评审与验收清单，如果功能规范满足该项标准，则勾选该项；如不满足，则留空。
```

要善用与Claude Code的互动机会，及时澄清和提问，不要把它的第一次输出当作最终结果。

### **第三步：生成实施计划**

此时，你可以明确技术栈和其他技术要求。可以利用项目模板自带的 `/plan` 命令，并配合如下提示：

```text
我们将使用 .NET Aspire 进行开发，数据库采用 Postgres。前端使用 Blazor Server，支持任务看板的拖拽操作和实时更新。需要创建REST API，包括项目API、任务API和通知API。
```

这一步的输出会包含多份实现细节文档，目录结构大致如下：

```text
.
├── CLAUDE.md
├── memory
│	 ├── constitution.md
│	 └── constitution_update_checklist.md
├── scripts
│	 ├── check-task-prerequisites.sh
│	 ├── common.sh
│	 ├── create-new-feature.sh
│	 ├── get-feature-paths.sh
│	 ├── setup-plan.sh
│	 └── update-claude-md.sh
├── specs
│	 └── 001-create-taskify
│	     ├── contracts
│	     │	 ├── api-spec.json
│	     │	 └── signalr-spec.md
│	     ├── data-model.md
│	     ├── plan.md
│	     ├── quickstart.md
│	     ├── research.md
│	     └── spec.md
└── templates
    ├── CLAUDE-template.md
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

请检查 `research.md` 文档，确保所用技术栈符合你的要求。如果发现有不合适的部分，可以让Claude Code进一步优化，甚至让它检查本地已安装的平台或框架（如 .NET）的版本。

此外，如果你选择的技术栈变化较快（如 .NET Aspire、JS 框架等），也可以让Claude Code帮你查找相关的最新资料，提示如下：

我希望你能仔细审查实施计划和具体细节，找出哪些地方由于.NET Aspire库更新频繁，可能需要进一步调研。对于你发现需要补充调研的部分，请在调研文档中补充关于本次Taskify应用将要使用的具体版本信息，并为每个细节分别发起并行的调研任务，利用网络资源查明相关细节。

在这个过程中，你可能会发现Claude Code在调研时方向跑偏——你可以用类似下面的提示语纠正它：

我认为我们需要把这个过程拆解成几个步骤。首先，列出在实施过程中你不确定、或者需要进一步调研的任务清单。把这些任务一一写下来。然后针对每一项任务，分别启动独立的调研任务，这样我们就能并行调研所有这些具体问题。我发现你刚才是在泛泛地调研.NET Aspire，这样太宽泛了，对我们帮助不大。调研必须聚焦于具体、明确的问题，才能真正解决实际难题。

> [!NOTE]
> Claude Code有时会过于积极，添加你并未要求的组件。此时应让它说明变更的理由和依据。

### **第4步：让Claude Code校验方案**

方案制定好后，你应让Claude Code整体过一遍，确保没有遗漏。可以用如下提示：

现在请你审查一下实施计划和实施细节文件。仔细阅读，判断是否有明显需要执行但被遗漏的任务。例如，在查看核心实现部分时，最好能在实施细节中引用相应位置，便于每一步在核心实现或细化过程中查找所需信息。

这样可以进一步完善实施方案，避免Claude Code在规划阶段遗漏关键环节。初步完善后，再让Claude Code根据清单检查一遍，确保万无一失，才能进入正式实施阶段。

如果你已经安装了[GitHub CLI](https://docs.github.com/en/github-cli/github-cli)，还可以让Claude Code直接从当前分支创建一个到`main`的Pull Request，并附上详细说明，以便整个过程有据可查。

>[!NOTE]
>在让智能体执行实现之前，建议先让Claude Code帮你复查方案细节，看看是否有过度设计的部分（要注意，它有时会过于积极）。如果发现有不必要的复杂设计，可以让Claude Code帮你简化。务必确保Claude Code在制定方案时，始终以[宪章](base/memory/constitution.md)为基本准则。

### 第五步：实现

准备就绪后，指示Claude Code开始实现你的方案（示例路径如下）：

```text
implement specs/002-create-taskify/plan.md
```

Claude Code会立即开始执行，实现你的方案。

>[!IMPORTANT]
>Claude Code会在本地执行CLI命令（如 `dotnet`），请确保你的电脑已安装相关工具。

实现完成后，让Claude Code尝试运行应用，并解决可能出现的构建错误。如果应用能运行，但出现了Claude Code无法直接通过CLI日志获取的运行时错误（比如浏览器日志中的报错），可以将错误信息复制粘贴给Claude Code，让它帮你排查。

</details>

---

## 🔍 故障排查

### Linux下的Git凭据管理器

如果你在Linux系统上遇到Git认证问题，可以安装Git Credential Manager：

```bash
#!/usr/bin/env bash
set -e
echo "正在下载 Git Credential Manager v2.6.1..."
wget https://github.com/git-ecosystem/git-credential-manager/releases/download/v2.6.1/gcm-linux_amd64.2.6.1.deb
echo "正在安装 Git Credential Manager..."
sudo dpkg -i gcm-linux_amd64.2.6.1.deb
echo "正在配置 Git 使用 GCM..."
git config --global credential.helper manager
echo "清理安装包..."
rm gcm-linux_amd64.2.6.1.deb
```

## 👥 维护者

- Den Delimarsky（[@localden](https://github.com/localden)）
- John Lam（[@jflam](https://github.com/jflam)）

## 💬 支持

如需支持，请在[GitHub issue](https://github.com/github/spec-kit/issues/new)中提交。我们欢迎Bug报告、新功能建议以及关于Spec-Driven Development的使用问题。

## 🙏 鸣谢

本项目深受[John Lam](https://github.com/jflam)的研究和成果启发与支持。

## 📄 许可证

本项目遵循MIT开源许可证。完整条款请参见[LICENSE](./LICENSE)文件。