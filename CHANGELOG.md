# Changelog

## v0.3.5 (2026-06-21)

### Fixed
- conceptual-example.md: 首次答对从 Good 改为「即时理解，待变式验证」
- procedural-example.md: splice 和 LRU 核心机制不再直接评 Good，独立完成保留 Good

### Added
- 项目驱动模式：references/project-driven.md
- 硬规则 13-15：项目驱动优先、最小教学、可验证产物
- 检查当前任务优先级增加「项目/探索目标」
- Reference 加载规则增加项目驱动触发条件

## v0.3.4 (2026-06-21)

### Changed
- user_profile.md 改为 example 模板 + 本地数据文件，.gitignore 保护个人数据
- 独立安装命令增加 mkdir -p 和 PowerShell 版本
- 「M2 模块」改为「项目深挖模块，编号不固定」
- 「ChatGPT 不纠错」改为「普通 AI 默认不保证长期教学闭环」
- 隐私保护默认建议 .git/info/exclude，不静默修改 .gitignore

### Added
- argument-hint 和显式 \$ARGUMENTS 支持
- 主题文件名规范化（移除非法字符，禁止路径穿越）
- C++ 示例知识地图接入初始化流程（优先读取 examples/）

### Fixed
- SKILL.md 版本号同步为 v0.3.3
- user_profile.md 隐私保护（与 Tracker 同级保护）

## v0.3.3 (2026-06-21)

### Changed
- 删除根目录 references/、examples/、knowledge/TEMPLATE.md，所有规则只存在于 .claude/skills/interview/
- README 目录树更新，删除已不存在的根 SKILL.md 和 references/
- '自带 Tracker' 改为 '首次运行自动创建个人 Tracker'
- '换技术栈' 和 '调规则' 指向 .claude/skills/interview/ 内的文件
- 英文 README 同步为三轮流程、A Typical Learning Loop、新安装说明

### Added
- knowledge/trackers/.gitkeep 保证目录在 git clone 后存在
- .claude/skills/interview/templates/gitignore-snippet 供独立安装时使用
- SKILL.md Tracker 初始化 6 步流程（建目录、保护隐私、复制模板、生成模块、确认、开始）

### Fixed
- 独立 Skill 安装后 Tracker 目录的 Git 隐私保护
- references/tracker.md 不再内嵌完整模板，改为链接 templates/tracker.md

## v0.3.2 (2026-06-21)

### Fixed
- 独立 Skill 打包为自包含（references/、examples/、templates/ 随 Skill 一起复制）
- 消除双 SKILL.md 同步风险（根目录 SKILL.md 删除，CLAUDE.md 指向唯一源）
- 修复 memory/MEMORY.md 残留的旧 Tracker 路径
- 修复默认 C++ Tracker 的 Git 跟踪风险（移至 knowledge/examples/）
- README 四层教学描述与 Skill 三轮流程统一
- "自动提醒"改为"启动时自动检查到期复习"
- "强制 AI"改为"持续约束 Claude"
- "题库"统一改为"知识地图与 Tracker"
- "看看实际效果"改为"一个典型的学习闭环"
- date 命令增加 PowerShell 兼容
- 英文 README 修复中英文混杂
- token 计费改为更准确的使用成本描述

## v0.3.1 (2026-06-21)

### Changed
- 统一 Tracker 路径为 knowledge/trackers/{主题}.md
- 明确产品形态：工作区模板 + 可独立安装的 Skill
- 重写 README：增加真实对话演示，8 个卖点收敛为 3 个核心能力
- 竞品对比改为"方案差异"
- 添加已知限制和设计原则章节

### Added
- MIT LICENSE 文件
- .gitignore（排除用户学习数据）

## v0.3.0 (2026-06-21)

### Added
- V3 学习引擎：分层教学、知识网络、四级评分、间隔复习
- SKILL.md 完整学习流程定义
- references/ 教学规则、知识网络、评分复习、tracker规范、常见错误
- examples/ 概念型和程序型教学示例
