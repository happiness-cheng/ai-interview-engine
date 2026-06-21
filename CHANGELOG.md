# Changelog

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
