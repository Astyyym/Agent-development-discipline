# Agent Development Discipline

## AI Agent 开发纪律

A reusable, framework-agnostic workflow for AI coding agents that need to develop and deliver software carefully.

一套可复用、与框架无关的 AI 编程 Agent 开发与交付流程，帮助 Agent 更谨慎地完成软件项目。

It helps an AI agent:

它帮助 AI Agent：

- confirm material requirements before coding;
- 在编码前确认重要需求；
- keep one authoritative source location;
- 保持唯一的权威源码位置；
- make small changes in independently verifiable stages;
- 将改动拆成可独立验证的小阶段；
- use real feedback loops and vertical slices;
- 使用真实反馈闭环和垂直切片；
- review requirements fit separately from engineering quality;
- 将需求符合性与工程质量分开审查；
- avoid speculative abstractions and unnecessary process overhead;
- 避免臆测式抽象和不必要的流程负担；
- verify the authoritative copy before cleaning temporary worktrees;
- 清理临时 worktree 前验证权威副本；
- scan for secrets, personal information, local paths, and real data before publication;
- 发布前扫描密钥、个人信息、本机路径和真实数据；
- distinguish repository pushes, releases, packages, and platform acceptance tests.
- 区分仓库推送、Release、软件包和平台验收测试。

## Installation / 安装

Copy `SKILL.md` into your Hermes skills directory, for example:

将 `SKILL.md` 复制到 Hermes skills 目录，例如：

```text
~/.hermes/skills/software-development/agent-development-discipline/SKILL.md
```

The skill is intentionally generic. It contains no project-specific credentials, personal data, or machine-specific paths.

本 skill 刻意保持通用，不包含特定项目凭据、个人数据或特定机器路径。

## Scope / 适用范围

Use it when an AI agent starts, changes, migrates, packages, open-sources, reviews, or delivers a software project.

适用于 AI Agent 启动、修改、迁移、打包、开源、审查或交付软件项目的场景。

This is a compact workflow, not a mandatory issue tracker, interview ritual, commit policy, or framework. Adapt the planning files, testing seams, and delivery gates to the project while preserving the evidence and safety rules.

这是一套紧凑的开发流程，不强制要求使用 Issue Tracker、访谈仪式、固定提交规范或特定框架。可以根据项目调整计划文件、测试接缝和交付阶段门，但应保留证据和安全规则。

## Design Principles / 设计原则

> Understand first → make a small change → verify the real behavior → record the result → deliver honestly.
>
> 先理解 → 做小改动 → 验证真实行为 → 记录结果 → 如实交付。

The detailed workflow is defined in [`SKILL.md`](SKILL.md). Supporting procedures are in the [`references/`](references/) directory.

详细流程定义在 [`SKILL.md`](SKILL.md) 中，配套操作规程位于 [`references/`](references/) 目录。

## License / 许可证

MIT
