# Claude Code 配置：换电脑 / 换成 Codex

记「装了什么、从哪装」。自己加的 skill 直接放在本仓库的 `skills/` 里，其余都从网上装。

更新于 2026-09-25。

## 装了什么

| 插件 | 来源（marketplace） | 状态 | 用来干什么 |
|---|---|---|---|
| oh-my-claudecode（OMC） | [Yeachan-Heo/oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode) | 启用 | agent 分工（executor、code-reviewer）、HUD 状态栏、ai-slop-cleaner |
| superpowers | 官方 `claude-plugins-official` | 启用 | brainstorming、systematic-debugging、写计划 / 执行计划 |
| ponytail | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 启用 | 只写需要的代码，能少写就少写 |
| taste-skill | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | 启用 | 前端设计：redesign、taste、minimalist |
| ECC | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | **停用** | 284 个 skill 加一大堆钩子，太重；常用的 5 个 skill 单独拷出来了 |

自己加的 skill：本仓库 `skills/` 下 13 个，跟本机 `~/.claude/skills/` 一样（`synced`、`learned` 不算）。

| skill | 来源（以后想更新时去这里拿） |
|---|---|
| animation-vocabulary、apple-design、emil-design-eng、find-animation-opportunities、improve-animations、pick-ui-library、review-animations | [emilkowalski/skills](https://github.com/emilkowalski/skills) |
| make-interfaces-feel-better、frontend-design-direction、accessibility、strategic-compact、liquid-glass-design | ECC 的 `skills/` 目录 |
| design-md | 照 [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) 整理的（74 个大厂的 DESIGN.md） |

docx、pdf、pptx、xlsx、skill-creator，以及 `skills/synced` 里的，都跟着 claude.ai 账号走，登录就有。

本机的 skill 有增减时，在仓库目录里跑一下再提交：

```bash
rsync -a --delete --exclude synced --exclude learned --exclude .DS_Store ~/.claude/skills/ skills/
```

## 一、换电脑（还用 Claude Code）

1. 装插件（每行分开跑）：

   ```bash
   claude plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode.git
   claude plugin marketplace add https://github.com/Leonxlnx/taste-skill.git
   claude plugin marketplace add DietrichGebert/ponytail
   claude plugin marketplace add https://github.com/affaan-m/everything-claude-code.git
   claude plugin install oh-my-claudecode@omc
   claude plugin install superpowers@claude-plugins-official
   claude plugin install taste-skill@taste-skill
   claude plugin install ponytail@ponytail
   claude plugin install ecc@ecc
   claude plugin disable ecc@ecc
   ```

2. 在 Claude Code 里跑一次 `/oh-my-claudecode:omc-setup`，它会写好全局 `CLAUDE.md` 和 HUD 状态栏。
3. `~/.claude/settings.json` 里补两项：`"effortLevel": "high"`，`"env": { "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1" }`（OMC 的 team 功能要用）。
4. 拷 skill（在本仓库目录里跑）：

   ```bash
   mkdir -p ~/.claude/skills && cp -R skills/. ~/.claude/skills/
   ```

## 二、换成 Codex

- **自己的 skill**：SKILL.md 格式是通用的，把本仓库 `skills/` 下的 13 个文件夹拷到 `~/.codex/skills/` 就能用。
- **superpowers**：有官方 Codex 版，直接装。
- **ponytail**：有 Codex 版，直接装。
- **ECC**：有官方 Codex 版，可以直接装。常用的 5 个 skill 已经跟着第一条拷过去了，所以一般不用装整个 ECC。
- **taste-skill**：没有 Codex 插件包，但它本身就是一堆 SKILL.md，把仓库 `skills/` 下的文件夹拷进 `~/.codex/skills/` 就能用。
- **OMC**：只能在 Claude Code 里用。同一个作者做了 Codex 版 [oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex)（OmX），功能类似（钩子、agent 团队、HUD），但是另一个项目，得重新配。
- **全局规则**：Codex 读的是 `~/.codex/AGENTS.md`。`~/.claude/CLAUDE.md` 里 OMC 那一大段是给 Claude Code 编排 agent 用的，不要照搬，只挑通用的偏好写进去，比如用中文交流。
- **自动模式规则、状态栏、ECC 钩子**：Codex 没有对应的东西，不迁。

在本仓库目录里跑：

```bash
mkdir -p ~/.codex/skills && cp -R skills/. ~/.codex/skills/
git clone https://github.com/Leonxlnx/taste-skill /tmp/taste-skill
for d in /tmp/taste-skill/skills/*/; do cp -R "${d%/}" ~/.codex/skills/; done
codex plugin marketplace add obra/superpowers
codex plugin add superpowers@superpowers-dev
codex plugin marketplace add DietrichGebert/ponytail
codex plugin add ponytail@ponytail
npm install -g oh-my-codex
omx setup --scope user
```

要装整个 ECC 的话再加：

```bash
codex plugin marketplace add affaan-m/everything-claude-code
codex plugin add ecc@ecc
```
