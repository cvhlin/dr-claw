# 安全扫描方案（Repo + History）

**负责人**: SL (Security/Compliance Lead)  
**协作**: EL

## 目标

- 确保仓库及（在可行范围内）历史提交中无高危 secrets 泄露。
- 明确扫描工具、执行人、处置流程。

## 扫描工具

| 用途 | 工具 | 说明 |
|------|------|------|
| 当前代码与未提交文件 | [gitleaks](https://github.com/gitleaks/gitleaks) 或 [trufflehog](https://github.com/trufflesecurity/trufflehog) | 任选其一，优先 gitleaks（轻量） |
| 历史提交 | 同上，对全历史运行（如 `gitleaks detect --no-git --source .` 或对 `git log -p` 做扫描） | 若历史含泄露，见处置流程 |
| 正则/简单模式 | 自定义规则（API key 前缀、Bearer、私钥文件等） | 工具未安装时的降级方案 |

## 执行人

- **日常/PR 前**: EL 或提交者本地运行扫描。
- **正式发布前**: SL 执行全仓+历史扫描并产出报告。

## 处置流程

1. **发现疑似泄露**
   - 立即标记为高危，通知 PL 与 EL。
   - 若为有效 token/密钥：立即在对应平台撤销或 rotate，再修复代码（移除或改为环境变量/secret 存储）。
2. **历史中已泄露**
   - 若密钥已 rotate，在 NOTICE 或安全文档中注明“某段历史曾泄露，已失效”。
   - 是否改写历史（如 `git filter-repo`）由 PL 决策；若上游或合规要求必须改写，由 EL 执行并通知全员。
3. **误报**
   - 在规则或排除列表中标注，避免重复误报；不提交真实密钥。

## 门禁

- 发布门禁：**无高危 secrets 泄露**（扫描报告零高危项）方可 Go。

## 降级（Day1 若工具未就绪）

- 先用基础正则扫描（如匹配 `AKIA|ghp_|sk-` 等常见前缀）与人工检查 `.env*`、`config*` 未被提交。
- Day2 前补全 gitleaks/trufflehog 与全历史扫描。
