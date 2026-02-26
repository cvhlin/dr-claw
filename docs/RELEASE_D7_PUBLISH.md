# D7-1: 推送 Public Repo 并打 v0.1.0 Tag

**执行人**: EL  
**协作**: PL  
**远端仓库**: https://github.com/bbsngg/VibeLab-beta

## 验收标准

- GitHub Release 可见
- 安装路径可用（clone + npm install + npm run dev 或 vibelab）

## 操作步骤（本地已就绪后）

1. **确认门禁**
   - 合规：LICENSE、NOTICE 完整
   - 安全：无高危 secrets（见 docs/SECRETS_SCAN_REPORT.md）
   - 可用：Quickstart 盲测通过
   - 质量：CI 全绿

2. **推送并打 tag**
   ```bash
   git remote add origin https://github.com/bbsngg/VibeLab-beta.git
   # 若已存在 origin，确保 URL 为上述地址：git remote set-url origin ...
   git push -u origin main   # 或 master，与远端默认分支一致
   git tag v0.1.0
   git push origin v0.1.0
   ```

3. **创建 GitHub Release**
   - 在 GitHub 仓库 → Releases → Create a new release
   - Tag: `v0.1.0`
   - Title: `Vibe Lab v0.1.0`
   - 描述：从 [docs/RELEASE_NOTES_v0.1.0.md](RELEASE_NOTES_v0.1.0.md) 复制内容（可略作精简）

4. **发布后**
   - 若发现关键 bug：修好后打 `v0.1.1` 并发布新 Release。
