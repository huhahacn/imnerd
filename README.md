# imnerd

让 AI 回答里的黑话，变成**大白话 + 一个具体例子**。

一个 [Agent Skill](https://code.claude.com/docs/en/skills)（`SKILL.md` 格式，DSH / Claude Code / Codex 通用）。

## 解决什么

AI 默认爱写「该接口采用异步消息队列解耦，并通过失败重试与死信队列保证最终一致性」这种话。装上之后：

> **改前**：该方案不具备可扩展性。
>
> **改后**：现在 100 个用户能跑，1000 个就卡死，因为每加一个用户都要改一次代码。

核心原则一句话：**术语不是不能出现，是不能裸奔。** 第一次出现 = 一句白话 + 一个例子，之后随便用。

## 什么时候触发

- 用户说：说人话 / 大白话 / 听不懂 / 太专业 / 什么意思 / 举个例子 / ELI5
- 受众不是同行：客户、老板、产品、运营、新人
- 一条回答里出现 ≥3 个没解释的术语或缩写
- 写给人类看的文档：README、方案、周报、邮件、交付说明

## 里面有什么

| 段落 | 内容 |
|---|---|
| 铁律 | 读者不看文档就能懂 —— 做不到就改，别发出去 |
| 三步改写 | 圈黑话 → 换句式（名词→动词、被动→主动、抽象→具体数字）→ 配例子 |
| 句式模板 | 「提升系统可用性」→「服务少挂：每月 4 小时 → 5 分钟」 |
| 术语表 | 20 条现成翻译：幂等、缓存击穿、熔断、灰度、事务、技术债、闭环、赋能、SLO、P0/P1… |
| 3 组前后对比 | 技术 / 职场 / 数据 |
| 30 秒自检 | 缩写展开了吗、有具体例子或数字吗、单句 ≤25 字、长度 ≤1.5 倍 |
| 别做过头 | 不牺牲精度、不幼稚化、代码命令 API 名原文照抄、用户用术语就跟着用 |
| 借口表 | 挡掉「用户是工程师不用解释」这类偷懒 |

## 安装

DSH 读取四个技能根目录（任选一个）：

```powershell
# 全局：所有项目都能用
git clone https://github.com/huhahacn/imnerd "$env:USERPROFILE\.agents\skills\imnerd"

# 只给当前项目用
git clone https://github.com/huhahacn/imnerd ".\.dsh\skills\imnerd"
```

| 工具 | 技能根 |
|---|---|
| DSH | `~/.dsh/skills/`、`~/.agents/skills/`、`<项目>/.dsh/skills/`、`<项目>/.agents/skills/` |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.agents/skills/` |

也可以手动把 `SKILL.md` 放到 `<技能根>\imnerd\SKILL.md`。

## 用法

装好即自动触发（`SKILL.md` 里 description 那行就是触发条件）。想手动叫：DSH 里输入 `/imnerd`，或直接说「用 imnerd 改写这段话」。

也可以只当模板抄：`SKILL.md` 里的术语表和前后对比示例，直接拿来当写作清单用。

## 许可

MIT，见 [LICENSE](LICENSE)。随便用、随便改、随便发。
