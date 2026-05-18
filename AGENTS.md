# AGENTS.md

本文件约束 agent 在 `auto_research` 框架源 repo 中工作时的行为。默认使用中文交流；代码字段、文件名、ID 和 schema 字段使用英文。

## 1. 当前定位

`auto_research` 是科研自动化框架的 MVP 源 repo。它不是具体科研项目，也不是完整 runtime。当前目标是沉淀可被具体项目通过 git submodule 消费的规则、模板、示例和 agent 协议。

不要在本 repo 中保存某个真实项目的实验进度。真实研究状态应保存在 consumer repo 的 `research/` 目录中。

## 2. 分层边界

- **Framework repo**：通用生命周期、模板、agent 角色、gate、profile 指南和示例。
- **Consumer project**：真实项目的 profile、state、research cards、实验输出和 manuscript。
- **Skill**：未来的薄适配层，用于指导 agent 使用本框架；MVP 阶段不先创建 skill。
- **Engineering runtime**：未来才做，用于 ID 生成、索引、校验、迁移和任务队列；MVP 阶段不先实现。

## 3. 修改原则

- 优先保持 Markdown 文件可读、可 diff、可被 agent 直接使用。
- 新规则必须说明适用阶段、触发条件和失败风险。
- 不把单个项目的领域规则写进通用模板；领域规则应放进项目 profile。
- 示例项目可以是虚构的最小研究链路，但必须展示分支、证据和 claim 绑定。
- 不自动改写历史 cards；只能追加 revision 或 migration note。

## 4. Agent 协作原则

默认不要堆多个 agent。角色按 gate 启用：

- 普通整理：主 agent。
- 新 experiment：student-executor + pi-reviewer。
- 失败复盘：student-executor + pi-reviewer，必要时 method-specialist。
- claim 或 manuscript：pi-reviewer + claim-auditor，必要时 writing-agent。
- 框架升级：orchestrator + repro-auditor 检查 consumer 状态兼容性。

多学生只用于任务可并行且文件责任边界明确的情况。多导师只用于路线转向、核心 claim、重大失败归因或 publish 前。

## 5. 证据和表述

所有研究结论必须区分：

- 已验证事实
- 推断
- 限制
- 竞争解释
- 下一步

claim 必须链接 evidence。没有 evidence 的 claim 只能标记为 `speculative`，不能进入强表述 manuscript。

## 6. MVP 约束

当前不要加入：

- CLI
- SQLite
- Web UI
- 自动迁移
- 自动任务队列
- 完整多 agent runtime

只有当文件型 MVP 在真实项目中暴露出稳定重复痛点后，才把对应部分工程化。

