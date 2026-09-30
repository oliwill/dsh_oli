## 本轮进度与下一步
<!-- memory:mem_c361e5b390e5270415d757d775ff6d31 -->
type:progress
当前状态（2026-09-30 17:15 全部复测完成）：
- 13 个 desktop 插件全部就位：8 个原功能正常 + builtin-browser（electron 二进制修复后 provider 正常，browser_session/browser_open 实测通过）+ tool-github（已绑定 @oliwill，token 已入库）+ files-panel（存疑）。
- 用户三批插件方案执行完毕；dsh-quant 按用户意愿暂缓。
- 遗留两项：① files-panel 是否实际生效待用户 GUI 目视确认，无效则 remove；② web profile 残留重复的 files-panel/tool-github 未清理。

下一步（可直接执行的第一步）：
1. 用户确认 files-panel：GUI 侧栏无文件面板 → 执行 dsh plugin --profile desktop remove @jiayuw/dsh-files-panel。
2. 按需清理 web profile：dsh plugin --profile web remove @jiayuw/dsh-files-panel @dsh-external/dsh-tool-github。
3. 待办增强项：ui-appearance 壁纸参数配置（Scrim 25–35%、Glass 14–18px 等）与定制 2560×1440 壁纸生成。