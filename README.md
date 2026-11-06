# work-artifacts

管理 AI 任务产生的临时文件、缓存、日志、下载包和构建中间产物，让项目目录保持整洁，并在任务结束时完成清理或明确报告遗留内容。

## 核心规则

- 使用当前项目已有的 `.work` 目录。若目录不存在，先告知绝对路径，由用户自行创建并核实后再使用。
- 临时脚本、草稿、截图、预览、日志、缓存、下载和解压内容放入已确认的临时目录；最终交付成果放在用户指定的位置。
- 用户明确指定其他临时目录时，按用户指定的位置执行，同样记录、清理并报告遗留内容。
- 使用已有 `.work` 前先盘点内容，只清理本次任务产生且已无用途的文件，保留其他任务的内容和 `.work` 根目录。
- 工具必须在其他位置生成文件时，提前说明路径和原因，并跟踪这些文件。构建、下载、解压和批量生成时检查体积变化。
- 直接删除被自动审批、权限、文件占用或工具限制拦截后，停止处理该项；不要改用回收站、更换删除方式或反复尝试绕过限制，列出清单交由用户自行删除。
- 结束前实际核对清理结果。需要保留或无法删除的临时内容，必须在最终回复中说明绝对路径、用途、已知文件数量与体积、保留原因和后续处理方式；数量或大小未知时明确说明，不为补齐统计长时间扫描或重试。
- 仅进行只读操作、原位编辑或生成最终交付文件时，无需为此要求创建 `.work`。

完整要求见 [SKILL.md](SKILL.md)。

## 安装

将本仓库放入客户端的 skills 目录，目录名保持为 `work-artifacts`。

Codex（PowerShell）：

```powershell
git clone https://github.com/Tristan-l0ng/work-artifacts.git "$env:USERPROFILE\.codex\skills\work-artifacts"
```

Claude Code（PowerShell）：

```powershell
git clone https://github.com/Tristan-l0ng/work-artifacts.git "$env:USERPROFILE\.claude\skills\work-artifacts"
```

也可以通过 CC Switch 的 Skills 页面导入仓库目录，再按客户端启用。若对应目录已经存在，请先检查已有内容，避免覆盖自己的修改。

## 使用

在任务中明确指定技能，例如：

```text
使用 $work-artifacts 管理这次任务的临时文件，结束前清理并报告仍需保留的内容。
```

这个技能是一组工作流程指令，不需要额外安装运行依赖。

## 仓库内容

- `SKILL.md`：技能说明和完整规则。
- `agents/openai.yaml`：技能显示名称、简短说明和默认提示词。
- `.gitignore`：忽略任务临时目录 `.work/`。
