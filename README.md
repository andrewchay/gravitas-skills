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

## 安装

**Gravitas / Claude Code Marketplace：**

在 Gravitas Marketplace 或 Claude Code 中添加 marketplace：

```
andrewchay/gravitas-skills
```

然后安装 `ste-writing` 插件。

**skills CLI：**

```bash
npx skills add andrewchay/gravitas-skills@ste-writing
```

## 目录结构

```
├── .claude-plugin/marketplace.json      # marketplace manifest
├── plugins/ste-writing/                 # Claude plugin 布局
│   ├── .claude-plugin/plugin.json
│   └── skills/ste-writing/SKILL.md
└── ste-writing/SKILL.md                 # skills.sh 布局（canonical 副本）
```

> 维护约定：`ste-writing/SKILL.md` 与 `plugins/ste-writing/skills/ste-writing/SKILL.md` 内容保持一致，改动时同步两份。
