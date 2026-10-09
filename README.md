# gravitas-skills

Andrew Chay 的个人技能仓库，同时兼容两种安装方式：

1. **Gravitas / Claude Code Marketplace**（Claude plugin marketplace 规范）
2. **skills.sh 开放生态**（`npx skills` CLI）

## 技能列表

### ste-writing（v0.2.0）

ASD-STE100 简化写作 + 反 AI 腔改写工具。

- 规则来源：ASD-STE100 Simplified Technical English, Issue 9（2025-01-15）核心写作规则 + 12 条反 AI 腔病灶清单
- 三种模式：**改写**（信息零丢失重写）/ **写作**（BLUF 结构起草 + 自检）/ **体检**（逐条病灶诊断）
- 中英文通用；官方规格对照：Part 1 共 9 节 53 条规则，词典 875 批准词 + 1274 非批准词

### asd-ste100（v0.4.0，vendored 自第三方）

> 来源：[danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill)（MIT，上游 commit `32511c6`，2026-10-04）

- 面向**被 Agent/机器解析的英文**的去歧义改写：工具描述、报错信息、Agent 间指令、系统提示词
- strict / STE-flavored 双模式 + before-after 示例 + `ste-lint.py` 检查脚本
- 与 ste-writing 互补：asd-ste100 管机器可解析性（英文），ste-writing 管输出风格（中英文）
- 遵守上游 IP 约定：只编码规则类别，不复制 ASD 官方词典
- **上游同步**：上游更新后重新拷贝 `skills/asd-ste100/` 内容并同步更新 plugin.json / marketplace.json 的版本号

### client-need-distillation（v1.0.0）

把客户沟通速记与碎片反馈蒸馏为可落地、高 ROI 的 AI 试点场景。

- **证据盘点**：每条信息标注 客户原话 / 档案记录 / 推断 三类——客户提及 ≠ 客户批准
- **速记 → 场景卡**：谁 / 现状 / 痛点 / AI 角色 / 数据依赖 / 可计量性
- **场景地图**：热度 × 数据可得 × 可计量 × 组织阻力 → 梯队（初步判断，非已证明排名）
- **需求纠偏（必做）**：服务结果为主指标，内部效率（FTE / 工时）降为次级经济指标，合规安全为硬约束
- **新增服务扫描**：过去因人力或协调成本做不了、现在 AI 能做的
- **N 角色思想实验**："只留 3 个角色留谁？"——其余职能重构为 client-facing Agent 网络（能力不可见，解决方案可见）
- **一周快赢**：一周内可落地 + ROI 一周内可观测 + client-facing 优先；一周只赌一个，赌赢滚动
- 源自危化品物流公司 FDE 实战，适用于任意 B2B AI 改造 / FDE 项目的需求梳理

## 安装

**Gravitas / Claude Code Marketplace：**

在 Gravitas Marketplace 或 Claude Code 中添加 marketplace：

```
andrewchay/gravitas-skills
```

然后安装 `ste-writing` 插件。

**skills CLI：**

```bash
npx skills add andrewchay/gravitas-skills@client-need-distillation
npx skills add andrewchay/gravitas-skills@ste-writing
```

## 目录结构

```
├── .claude-plugin/marketplace.json           # marketplace manifest
├── plugins/
│   ├── ste-writing/                          # Claude plugin 布局
│   │   ├── .claude-plugin/plugin.json
│   │   └── skills/ste-writing/SKILL.md
│   └── client-need-distillation/
│       ├── .claude-plugin/plugin.json
│       └── skills/client-need-distillation/SKILL.md
├── ste-writing/SKILL.md                      # skills.sh 布局（canonical 副本）
└── client-need-distillation/SKILL.md         # skills.sh 布局（canonical 副本）
```

> 维护约定：`ste-writing` 与 `client-need-distillation` 的根目录 `SKILL.md` 与 `plugins/<name>/skills/<name>/SKILL.md` 内容保持一致，改动时同步两份。
