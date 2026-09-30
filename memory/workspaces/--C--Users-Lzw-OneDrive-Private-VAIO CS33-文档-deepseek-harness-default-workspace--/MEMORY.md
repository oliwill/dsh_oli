
## 2026-09-30
- dsh CLI 未加入 PATH，实际入口为 "D:\Program Files (x86)\DSH\resources\runtime\cli\bin\dsh.cmd"；profiles 位于 C:\Users\Lzw\.dsh\profiles（desktop、web）
- 写 ~/.dsh 目录需 danger-full-access 沙盒提升；插件安装/变更后需重启 DSH 应用才能生效

## 2026-09-30
- dsh 插件 peerDependencies 不兼容时的处理路径：用户确认风险后执行 `dsh plugin allow-version --accept-risk` 登记版本豁免再安装；豁免仅对"该插件版本 + 该 dsh 版本"组合有效

## 2026-09-30
- dsh CLI 实际入口为 D:\Program Files (x86)\DSH\resources\runtime\cli\bin\dsh.cmd（不在 PATH）；插件 peer 版本冲突的既定处理方式是经用户确认后用 allow-version 登记精确豁免（tool-github 0.1.0 × dsh 0.2.0-rc.2 已登记）；用户贴的外部方案（含 ChatGPT 来源）中 npx @deepseek-ai/dsh 等安装命令不适用于本机

## 2026-09-30
- pnpm allowBuilds 白名单会拦截含二进制安装脚本的依赖（electron/prepare 类），表现为包已装但二进制缺失；修复模式是在 pnpm-workspace.yaml allowBuilds 加白后手动重跑对应 install 脚本