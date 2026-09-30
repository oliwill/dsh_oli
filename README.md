# dsh_oli — DSH 配置与记忆同步仓库

跨机器同步 DeepSeek Harness(DSH)的 profile 配置与 agent 记忆/项目进度。
推送源机器:Windows,DSH Desktop 0.2.0-rc.2,账号 @oliwill。最近同步:2026-09-30。

## 目录结构

```
profiles/desktop/     生效的桌面 profile(插件清单 13 项 + pnpm 配置 + 兼容豁免 + UI 补丁)
profiles/web/         web profile(遗留,与 desktop 部分重复)
memory/MEMORY.md      用户级长期记忆(跨项目规则)
memory/workspaces/*/  各工作区的项目笔记、每日日志、交接白板(PLAN.md)与账本
memory/hub/procedures.json + 各 workspace hub/  技能库(procedure memory)
```

## 新机器恢复步骤(Windows)

1. 安装 DSH Desktop 并首次启动一次(生成 `C:\Users\<你>\.dsh`)。
2. 把 `profiles/desktop/` 下的 4 个文件覆盖到 `%USERPROFILE%\.dsh\profiles\desktop\`。
3. 把 `memory\` 下内容覆盖到 `%USERPROFILE%\.dsh\memory\`(保持 workspaces 目录名原样——目录名编码了工作区绝对路径,新机器若工作区路径不同,新建对应目录或让 auto-memory 重建后再覆盖笔记内容)。
4. 重启 DSH Desktop。首次启动 pnpm 安装依赖时,`pnpm-workspace.yaml` 的 allowBuilds 已含 electron 等,二进制会正常装上。
5. 版本豁免:`compatibility.json` 已随仓库同步,tool-github 0.1.0 × dsh 0.2.0-rc.2 与 trading 三条豁免直接生效;若新机器 DSH 版本不同,需重新 `dsh plugin allow-version` 登记。
6. 需要手动重配的凭据(不入库,安全):
   - GitHub token:`github_bind` 重新绑定
   - LLM provider API key:设环境变量 `KIMI_CODING_API_KEY` / `ZAI_CODING_CN_API_KEY`(见 cordis.patch.yml,仅引用环境变量名,无明文密钥)

## 已知事项(2026-09-30)

- files-panel 未声明 dsh.bundle,可能不生效,待确认后可移除。
- web profile 残留与 desktop 重复的插件,未清理。
- trading bundle 行情数据目录默认 `profiles/desktop/data`(空),需按需在 cordis.patch.yml 覆写 root。

## 同步约定

改完配置/记忆后重新覆盖对应文件并推送;拉取时先用 git pull 再复制回 `%USERPROFILE%\.dsh\`。勿把凭据、node_modules、pnpm-lock 之外的本机缓存提交进来。
