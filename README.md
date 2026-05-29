# ai-interview-engine

用 Claude Code 搭建你的专属面试老师。不是陪聊，是严师。

[English](README_EN.md)

## 痛点：用 AI 准备面试的真实困境

你一定试过用 ChatGPT / Claude 准备面试：

- 你说了一堆，它回一句 "Great answer!" — **其实你答错了它不说**
- 每次打开新对话，它不记得你昨天学了什么 — **从零开始**
- 学了一堆知识点，不知道什么时候该复习 — **没有计划**
- 它给你讲概念，你看完觉得懂了，面试时却说不出来 — **没有验证**

根本原因：**ChatGPT 是一个贴心的陪聊，不是一个严格的老师。**

## 方案：用规则文件强制 AI 当严师

Claude Code 有一个独特能力：**规则文件（CLAUDE.md）+ 持久化记忆系统**。

通过规则文件，你可以强制 AI 的行为：
- 答错了必须讲解，不能糊弄说 "Great"
- 讲解完必须出验证题，确认你真懂了
- 每天学习的知识点要追踪，按遗忘曲线调度复习
- 学习进度跨会话保存，下次打开继续

**一套配置文件，让 Claude Code 变成一个有记忆、有计划、有原则的面试老师。**

## 前置条件

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)（CLI 工具）
- API key（Anthropic / OpenAI / 其他兼容 API 均可）
- Git（用于 fork 仓库）

## vs 竞品

| 能力 | ChatGPT 面试 | Anki | NotebookLM | SaaS 平台 | **本项目** |
|------|-------------|------|------------|----------|----------|
| 跨会话记忆 | 无 | 仅卡组级 | 无 | 部分 | **有** |
| 间隔重复 | 无 | 有 | 无 | 无 | **有** |
| 答错→讲解→验证 | 无 | 无（只给答案） | 无 | 部分 | **有** |
| 基于项目代码原生出题 | 需手动贴代码 | 不适用 | 需上传文件 | 不支持 | **原生支持** |
| 额外费用 | 无 | 无 | 无 | $29-300/次 | **无额外费用** |

> 本项目依赖 Claude Code，需要一个 API key。对比的是**额外费用**，不是总成本。

## 快速开始

### 1. Fork 仓库

```
gh repo fork <your-username>/ai-interview-engine --clone
```

或者直接下载 ZIP 解压到任意目录。

### 2. 用 Claude Code 打开

```bash
cd ai-interview-engine
claude
```

### 3. 开始第一次对话

输入：

> 我要准备 C++ 后端开发面试，目标是大厂实习。开始复习。

Claude 会读取你的规则文件和题库，开始第一轮出题。

### 4. 自定义你的内容

- **换技术栈**：复制 `knowledge/TEMPLATE.md` → `interview_tracker.md`，填入你的知识点
- **加项目**：在 `interview_tracker.md` 的 M2 模块填入你的项目关键设计决策
- **调规则**：编辑 `rules/interview.md` 修改讲解方式、出题数量等

## 目录结构

```
ai-interview-engine/
├── CLAUDE.md                    # 入口：全局规则 + 使用说明
├── README.md                    # 你正在看的这个文件
├── rules/
│   └── interview.md             # 核心规则：严格学习流程（三步法 + 遗忘曲线）
├── knowledge/
│   ├── interview_tracker.md     # C++ 示例题库（可替换为你的技术栈）
│   └── TEMPLATE.md              # 空白模板
└── memory/
    ├── MEMORY.md                # 记忆索引（自动维护）
    └── user_profile.md          # 用户画像模板
```

## 核心机制

### 三步学习法

```
出题 → 你回答
         ↓
      答对 → 下一题
      答错 → 讲解（含参考资料 URL）→ 出验证题 → 通过才出新题
```

### 每日收尾

```
说"今天就到这" → 给出今日大纲 → 你回忆 → 判断掌握程度 → 更新复习调度
```

### 遗忘曲线复习

```
首次学习 → D+1 → D+2 → D+4 → D+7 → D+15
每次会话开始时，自动检查哪些知识点该复习了
```

## 使用场景

- 秋招/春招技术面试准备
- 转行/跳槽面试复习
- 期末考试复习（原理相同，换知识点库即可）

## License

MIT
