# desktop-agent-self-recovery

帮助 Codex 在操作各类 Windows 桌面软件时衔接新窗口、从异常中恢复，并避免无效重复。

## 核心行为

- 界面变化后重新识别窗口与控件，继续已授权的任务。
- 操作无进展时先检查原因，同一异常最多执行两次恢复尝试。
- 保留最后成功步骤，从尚未完成的动作继续，避免重复创建、输入或提交。
- 确实无法继续时保留现场，说明原因和下一步建议。

## 文件

```text
desktop-agent-self-recovery/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── README.md
```

`SKILL.md` 包含通用操作规则；`agents/openai.yaml` 关闭自动调用，只有用户明确调用后才启用。

## 使用

将整个 `desktop-agent-self-recovery` 文件夹放入你的 Codex skills 目录，保留 `agents/openai.yaml`。在 Codex 中调用：

```text
使用 $desktop-agent-self-recovery 完成当前桌面任务。界面变化后重新识别并继续，操作无进展时先检查原因，从最后成功步骤恢复。
```

适用于通过已有桌面控制工具操作软件的任务，不绑定特定应用。

## 能力边界

这是指令型 Skill，依赖现有桌面工具，不包含后台监控或辅助脚本。它指导 Codex 的决策与恢复流程，无法保证底层工具故障时任务仍不中断。
