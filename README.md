# skill-creator-claude

> The best skill-creation methodology, available to everyone.

## 这是什么

这是 **Anthropic 为 Claude Code 内置的 skill-creator**，经过最小改动，使其可以在任何支持 subagent 的 agent 平台上运行。

原版 skill-creator 是 Anthropic 工程师精心设计的 skill 开发工具链，涵盖从草稿到测评、迭代、description 优化的完整闭环。我们认为这套方法论非常优秀，应当让更多人用上它——而不只是 Claude Code 的用户。

## 原版出处

- **原作者**：Anthropic
- **许可证**：Apache 2.0（见 [LICENSE](./LICENSE)）
- **原始来源**：Claude Code 客户端内置插件 (`~/.claude/plugins/marketplaces/claude-plugins-official/plugins/skill-creator`)
- **完整能力体验**：[Claude Code](https://claude.ai/code)（免费可用）

## 我们的原则

- **最小改动**：只移除无法跨平台运行的硬依赖，保留 100% 的方法论和工具脚本
- **保留归属**：Apache 2.0 要求的所有版权声明和 LICENSE 文件完整保留
- **普惠大众**：让没有使用过 Claude Code 的用户也能体验到最优秀的 skill 设计哲学
- **引流原版**：如果你想体验 100% 的功能，去用 Claude Code——这个版本是入口，不是替代

## 与原版的差异（变更日志）

我们只做了 **4 处修改**，改动量 < 10%，全部在 `skills/skill-creator/SKILL.md`：

| # | 修改内容 | 原因 |
|---|---|---|
| 1 | 文件头添加修改声明注释 | Apache 2.0 要求标注修改 |
| 2 | Description Optimization Step 3：添加平台说明，注明 `run_loop.py` 需要 `claude -p` CLI，提供无 CLI 时的手动替代方案 | `claude -p` 是 Claude Code 专有命令行工具 |
| 3 | "Package and Present" 章节：移除 `present_files` 工具的条件判断，直接运行 `package_skill.py` | `present_files` 是 Claude Code 专有工具 |
| 4 | 合并"Claude.ai-specific"和"Cowork-Specific"两个平台章节为统一的"Platform Notes"，移除末尾 TodoList 提示 | 统一跨平台说明，移除 Claude Code UI 专有功能引用 |

**未改动的内容**（即全部核心内容）：
- 完整的 skill 开发方法论
- 所有 Python 脚本（`run_eval.py`、`run_loop.py`、`improve_description.py` 等）
- eval viewer 和 benchmark 系统
- 测评流程、grading、blind comparison
- 所有 agent 子文件（`agents/grader.md`、`agents/comparator.md`、`agents/analyzer.md`）
- `references/schemas.md`

## 功能对比

| 功能 | 本版本 | Claude Code 原版 |
|---|---|---|
| Skill 起草与迭代 | ✅ | ✅ |
| 测评与 eval viewer | ✅（需 Python） | ✅ |
| Benchmark 对比 | ✅（需 subagents） | ✅ |
| Description 优化（improve） | ✅（需 `ANTHROPIC_API_KEY`） | ✅ |
| Description 触发率测试 | ❌ 需 `claude -p` CLI | ✅ |
| 打包 `.skill` 文件 | ✅ | ✅ |

## 使用方式

### 通过 ClawHub 安装
```bash
clawhub install plabzzxx/skill-creator-claude
```

### 手动安装
将 `skills/skill-creator/` 目录复制到你的 agent 平台的 skills 目录即可。

### Description 优化脚本（可选）
如需使用 `improve_description.py` 自动优化 description，需设置环境变量：
```bash
export ANTHROPIC_API_KEY=your_key_here
```

## 致谢

完整的设计思想、代码和方法论版权归 Anthropic 所有。本仓库是在 Apache 2.0 许可证下的 derivative work，目的是扩大受益范围，而非取代原版。

如果你觉得这个 skill 有价值，去试试 [Claude Code](https://claude.ai/code) 吧，那里有 100% 的完整体验。
