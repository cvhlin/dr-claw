# VibeLab v0.1.0 范围清单（冻结）

**生效日期**: 2026-02-21 (PL 确认)  
**公开仓库**: https://github.com/bbsngg/VibeLab-beta

## 做（In Scope）

- 本地/远程桌面与移动端 UI，支持 Claude Code、Cursor CLI、Codex
- Research Lab 概览：源论文、想法（Markdown+LaTeX）、流水线状态、缓存产物
- InnoFlow Skills：orchestrator、prepare-resources、idea-generation、code-survey、experiment-dev、experiment-analysis、paper-writing 等技能
- 聊天、终端、文件树、Git 管理、会话管理
- 通过 Quickstart 文档可在新机器上 10 分钟内启动并看到 UI
- 合规：GPL-3.0、上游归属（NOTICE）、无高危 secrets
- 基础 CI：`npm ci` / `typecheck` / `build` 通过后可合并
- 社区承接：GitHub Discussions 分类、Slack 工作区、CoC、SECURITY.md 与漏洞上报

## 不做（Out of Scope for v0.1.0）

- 非必须的新功能或大重构
- Idea/Experiments/Paper 看板完整数据打通（首版可单一数据源或占位）
- Skills taxonomy v2、非高频链路扩展
- 多语言文档全面对齐（以 README 为准，逐步对齐）
- 历史 git 的 rewrite（除非经 PL 决策为必须）

## 变更与升级

- 范围变更须 PL 拍板并更新本文档后同步全员。
- 需求膨胀时优先砍“不做”项或延后至 v0.2。
