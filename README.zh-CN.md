[English](README.md) · **中文**

# speak-human（说人话）

> *"说人话。"*

[![skills.sh](https://skills.sh/b/Haor/speak-human)](https://skills.sh/Haor/speak-human)

一个 [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)，给任何 AI agent 一套统一的沟通纪律：**说人话，同时保持诚实**——让每个实质性回答既读得懂，又能溯源核验。

不同的 agent（和不同的模型）会滑向两个相反的毛病。有的精准但读不懂——堆事实、甩分支名和行号、没有叙事，没有一句话告诉你这些**意味着什么**。有的流畅但过度自信——整齐的二分、生动的比喻、像"~85% 完成"这种体感数字被当成度量甩出来。`speak-human` 给这两种失败都起了名，追到各自的根因，把回答拉向校准的中点。

## 一条规则

> **校准（Calibration）**——说出的"量"和"确定性"，精确等于背后证据的"量"和"确定性"；包装到刚好能被读懂为止，不多不少。

```
  表达 < 证据                  表达 = 证据                  表达 > 证据
   欠表达                       目标·中点                     过度包装
   真，但读不懂            说多少懂多少、              顺，但不全真
                          懂多少有多少证据
```

它约束的是**"表达与证据的对齐度"**，而不是你的文风——所以同一套纪律能跨 agent、跨模型生效。

## 仓库内容

| 文件 | covers 什么 |
|---|---|
| `SKILL.md` | 核心：校准规则、四个不变量、坐标泛化表、两侧刹车、场景旋钮、塌缩阀、出门自检。 |
| `references/diagnosis.md` | *为什么*会失败——知识的诅咒、句子骨架的差异、流畅性把猜测洗成事实——以及如何规避。 |
| `references/report-mode.md` | 单向吸收：报告骨架 + 沟通工程工具箱。 |
| `references/discussion-mode.md` | 双向收敛：只在多轮对话里才重要的那些动作。 |
| `references/examples.md` | 每种失败模式的 before/after 重写。 |

## 核心理念

- **四个不变量**，每个回答都带上——意图、行动、发现、坐标。
- **按对象组织，不按证据类型组织。** 汇报"Git / 代码 / 测试 / 文档"会逼读者自己拼故事。按他关心的某功能/某 bug/某模块来组织，把坐标折进去。
- **诚实的坐标，泛化定义。** 每句话要么指向可核验的东西（`文件:行号`、真实命令+结果、精确 ref），要么戴推测帽子（`推测：` / 未核实）。推测的坐标，就是承认它是推测。
- **两侧刹车。** 偏欠表达就补沟通层（事实不动，只加包装）；偏过度包装就削掉或戴帽超出证据的部分——但保留有用的估计，只给它戴帽，别删掉。
- **两种模式。** *报告态*优化吸收；*讨论态*优化收敛，并加上自己的动作（承接、共建词汇、增量+对齐检查）。

## 安装

### 用 `skills` CLI（推荐）

```bash
npx skills add Haor/speak-human
```

支持 Claude Code、Codex、Cursor 等 70+ agent——CLI 会自动检测你装了哪些。`-g` 全局安装，`-a <agent>` 指定某个 agent（如 `-a claude-code`）。

### 手动安装

```bash
# 全局（所有项目可用）
git clone https://github.com/Haor/speak-human ~/.claude/skills/speak-human
```

当回答是一份实质性的报告、分析、状态盘点，或一段回答读着难懂或太滑时，skill 会自动触发。你也可以点名调用（"说人话" / "speak human"）。

## 许可证

MIT —— 见 [LICENSE](LICENSE)。
