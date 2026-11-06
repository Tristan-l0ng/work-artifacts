# work-artifacts

将成果放在对应项目位置，把任务产生的非成果文件集中到 `.work`，避免过程材料散落或被误当作交付成果。

## 核心规则

- 源码、必要配置、用户要求的最终成果和交付工具必需的简短使用说明，放在对应项目成果位置；其余过程材料统一放入本项目 `.work`。
- 临时脚本、草稿、日志、截图、预览、测试输出、下载与解压文件、构建中间产物和缓存，都属于非成果文件。工具支持输出或缓存目录参数时，直接指向 `.work`。
- 不得自行把排查计划、进度笔记、交接备忘等过程材料认定为成果。未经用户明确要求，不提交、打包、上传或发送这些材料，也不把其链接作为交付成果发送。
- 沿用当前项目已有的 `.work` 路径或明确约定。若目录不存在，先告知完整绝对路径，由用户自行创建并核实后再使用；只读或原位编辑无需为此创建 `.work`。
- 平时及项目结束时，不主动删除、盘点、扫描或统计临时文件，不建立台账或执行额外的清理验证。
- 用户要求清理时，只做判断所必需的最少查看，并直接在聊天中列出 `【待删除】完整绝对路径 + 一句用途或删除理由`；必要时标注 `【保留】`。默认由用户自行处理，不执行删除，不生成清理清单文件。
- Codex 初始配置中默认要求删除的内容，继续按原配置处理；本技能不覆盖或扩展这些默认规则。

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
使用 $work-artifacts 把非成果文件放入本项目 .work；只有我提出清理时，才在聊天中列出待处理的完整路径。
```

这个技能是一组工作流程指令，不需要额外安装运行依赖。

## 仓库内容

- `SKILL.md`：技能说明和完整规则。
- `agents/openai.yaml`：技能显示名称、简短说明和默认提示词。
- `.gitignore`：忽略任务临时目录 `.work/`。
