# 🔥 hot-seller · 让产品大卖特卖·销售大师技能包

汇集三位顶尖销售人物的思维框架，不是教你怎么喊「最后三件」，是教你怎么让用户主动想买。

## 三位大师

| 大师 | 销售哲学 | 核心武器 | 适用场景 |
|------|---------|---------|---------|
| 🟡 雷军 | 产品即销售 | 定价能力 + 数字化升维 | 高性价比产品、新品类破圈 |
| 🟢 董宇辉 | 内容即销售 | 情感连接 + 知识赋魅 | 品类同质化、面向情感消费群体 |
| 🔴 罗永浩 | 人格即销售 | 事件势能 + 坦承式信任 | 品牌建设、差异化产品 |

## 快速选人

| 你的产品特点 | 推荐人选 |
|------------|---------|
| 定价是核心竞争力 | 雷军 |
| 需要制造行业轰动 | 罗永浩 |
| 品类同质化严重 | 董宇辉 |
| 需要快速出货（直播带货） | 董宇辉 + 罗永浩 |
| 产品走高端路线 | 雷军 + 罗永浩 |
| 面对女性/家庭用户 | 董宇辉 |
| 面对男性/极客用户 | 雷军 + 罗永浩 |

## 目录结构

```
hot-seller/
├── SKILL.md                        ← 入口：选人指南 + 三位大师简介
├── lei-jun-perspective/
│   ├── SKILL.md                    ← 雷军：6个心智模型 + 8条启发式 + 完整案例
│   └── references/research/
├── dong-yuhui-perspective/
│   ├── SKILL.md                    ← 董宇辉：5个心智模型 + 7条启发式 + 完整案例
│   └── references/research/
└── luo-yonghao-perspective/
    ├── SKILL.md                    ← 罗永浩：5个心智模型 + 7条启发式 + 完整案例
    └── references/research/
```

## 安装说明

### Claude Code

将技能包克隆到 Claude Code 的 skills 目录：

```bash

# 全局安装（所有项目和agent都可用）
mkdir -p ~/.claude/skills
git clone git@github.com:konglong87/hot-seller.git ~/.claude/skills/hot-seller

```

安装后，在 Claude Code 中输入 `/hot-seller` 即可调用，或当你的提问涉及销售、定价、带货等触发词时自动激活。

### OpenCode

OpenCode 兼容 Claude Code 的 skills 目录，直接复用上面的安装方式：

```bash
# 项目级
mkdir -p .claude/skills
git clone git@github.com:konglong87/hot-seller.git .claude/skills/hot-seller

# 全局级
mkdir -p ~/.claude/skills
git clone git@github.com:konglong87/hot-seller.git ~/.claude/skills/hot-seller
```

OpenCode 也会读取项目根目录的 `AGENTS.md`，你可以在其中引用技能包：

```markdown
## 销售技能

当涉及销售策略、定价、带货等问题时，参考 `.claude/skills/hot-seller/SKILL.md` 中的三位大师视角。
```

### Cursor

在项目根目录创建 `.cursor/rules/` 目录，将技能包内容转为 `.mdc` 规则文件：

```bash
mkdir -p .cursor/rules
git clone git@github.com:konglong87/hot-seller.git /tmp/hot-seller
```

然后创建规则文件 `.cursor/rules/hot-seller.mdc`：

```markdown
---
description: "销售大师技能包：雷军/董宇辉/罗永浩三位销售视角的心智模型和话术建议"
alwaysApply: false
globs: []
---

参考 /tmp/hot-seller/SKILL.md 中的三位大师选人指南和心智模型。
当用户提问涉及销售、定价、带货、发布会策略时，根据产品特点选择对应大师视角。
```

> **提示**：Cursor 的 `.mdc` 规则文件支持 4 种激活模式（always / intelligent / glob / manual）。建议使用 `alwaysApply: false` 让 Agent 智能判断何时激活，避免浪费上下文。

### Codex（OpenAI）

Codex 通过 `AGENTS.md` 加载自定义指令。在项目根目录创建 `AGENTS.md`，引用技能包：

```bash
git clone git@github.com:konglong87/hot-seller.git /tmp/hot-seller
```

在项目根目录的 `AGENTS.md` 中添加：

```markdown
## 销售技能包

当涉及销售策略、定价、带货、发布会等问题时，参考以下三位大师视角：

- 雷军视角：极致性价比 + 预期差营销 + 数字化升维 → /tmp/hot-seller/lei-jun-perspective/SKILL.md
- 董宇辉视角：知识赋魅 + 情感定价 + 故事化销售 → /tmp/hot-seller/dong-yuhui-perspective/SKILL.md
- 罗永浩视角：颠覆式情绪共鸣 + 坦承式信任 + 事件制造力 → /tmp/hot-seller/luo-yonghao-perspective/SKILL.md

选人指南见 /tmp/hot-seller/SKILL.md
```

> **提示**：Codex 也支持全局指令文件 `~/.codex/AGENTS.md`，可将上述内容放入全局文件让所有项目共享。

### OpenClaw

OpenClaw 原生支持 SKILL.md 格式，直接安装：

```bash
# 从 Git 仓库安装到 workspace
openclaw skills install git:konglong87/hot-seller

# 或全局安装（所有 agent 共享）
openclaw skills install git:konglong87/hot-seller --global

# 或手动安装
git clone git@github.com:konglong87/hot-seller.git ~/.openclaw/skills/hot-seller
```

安装后，在 OpenClaw 中输入 `/hot-seller` 即可调用，或当提问涉及销售触发词时自动激活。

> **提示**：OpenClaw 的技能加载优先级为：workspace skills > project agent skills > personal agent skills > managed skills > bundled skills。全局安装放在 `~/.openclaw/skills/`，项目级放在 `<workspace>/skills/`。

## 版本

v1.1.0

## 调研截止

2026年6月10日

