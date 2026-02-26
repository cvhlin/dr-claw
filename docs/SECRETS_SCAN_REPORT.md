# Secrets 扫描报告（D2-1）

**执行日期**: 2026-02-21  
**执行人**: SL  
**范围**: 全仓当前文件 + 全历史（431 commits）

## 工具

- gitleaks v8.21.2（全历史扫描）
- 基础正则 + 人工检查（补充验证）

## 结果

- **高危项**: 0
- **gitleaks 输出**: `431 commits scanned. no leaks found`
- **说明**: 代码中出现的 `ghp_xxx...` 为 UI 占位符（i18n/common.json、ProjectCreationWizard.jsx），非真实 token。`.env` / `.env.example` 仅含注释与变量名，无明文密钥。

## 门禁

- 发布前复扫，保持高危项为 0。
- 复扫命令：`gitleaks detect --source . --verbose`
