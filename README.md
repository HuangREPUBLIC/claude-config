# Claude Code 配置：换电脑 / 换成 Codex

记「装了什么、从哪装」。自己加的 skill 直接放在本仓库的 `skills/` 里，其余都从网上装。

更新于 2026-11-19。插件版本：OMC 5.8.4（固定版本，见下）、ponytail 5.3.3、taste-skill 2.5.1、ECC 2.2.3（停用）。

## 装了什么

| 插件 | 来源（marketplace） | 状态 | 用来干什么 |
|---|---|---|---|
| oh-my-claudecode（OMC） | [Yeachan-Heo/oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode) | 启用 | agent 分工（executor、code-reviewer）、HUD 状态栏、ai-slop-cleaner |
| ponytail | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 启用 | 只写需要的代码，能少写就少写 |
| taste-skill | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | 启用 | 2.5 起只剩一个 `taste-skill`，专做企业官网（带 Stop 钩子和 Chrome 检查脚本）；以前的 minimalist、redesign 已拷进本仓库 `skills/` |
| ECC | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | **停用** | 284 个 skill 加一大堆钩子，太重；常用的 5 个 skill 单独拷出来了 |

不装的：superpowers（2026-11-19 卸了，跟 OMC 重复：头脑风暴、写计划、调试、验证 OMC 都有，两套一起开还会多加载一大段启动说明）；graphify（项目都在 2 万行以内，LSP 够用）；agency-agents 整套（跟 OMC 的 agent 重复，只挑了 3 个，见下面）。

**分工**：编排 / 计划 / 验证归 OMC；写代码的风格归 ponytail；设计按平台分，iOS 用 apple-design、liquid-glass-design、make-interfaces-feel-better，网页用 minimalist-ui、redesign-existing-projects（从 taste-skill 1.0.0 拷出来的），两边不混用。

自己加的 skill：本仓库 `skills/` 下 19 个，跟本机 `~/.claude/skills/` 一样（`synced`、`learned` 不算）。

| skill | 来源（以后想更新时去这里拿） |
|---|---|
| animation-vocabulary、apple-design、emil-design-eng、find-animation-opportunities、improve-animations、pick-ui-library、review-animations、write-swift、mobile-native | [emilkowalski/skills](https://github.com/emilkowalski/skills) 的 `skills/`。write-swift 给 Climb（Swift 6 并发、性能、Swift Testing），mobile-native 给手机上用的网页系统 |
| minimalist-ui、redesign-existing-projects | taste-skill 1.0.0 的 `skills/minimalist-skill`、`skills/redesign-skill`。上游 2.5 已删，以后不用再更新 |
| make-interfaces-feel-better、frontend-design-direction、accessibility、strategic-compact、liquid-glass-design | ECC 的 `skills/` 目录 |
| design-md | 照 [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) 整理的（74 个大厂的 DESIGN.md） |
| grill-me、grilling | [mattpocock/skills](https://github.com/mattpocock/skills) 的 `skills/productivity/`（只挑了这两个，没装整套）。动手前输入 `/grill-me`，让 AI 一轮轮盘问方案，每题带推荐答案 |

自己加的 agent：本仓库 `agents/` 下 3 个，从 [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) 挑的，补 OMC 没有的产品和用户视角。`name` 改成了小写加短横线，颜色改成颜色名。

| agent | 原文件 | 用来干什么 |
|---|---|---|
| product-manager | `product/product-manager.md` | 功能取舍、排优先级、写需求文档 |
| ux-researcher | `design/design-ux-researcher.md` | 可用性分析、整理用户反馈 |
| persona-walkthrough | `design/design-persona-walkthrough.md` | 扮演某个用户逐屏走一遍页面，偏营销落地页的转化分析 |

docx、pdf、pptx、xlsx、skill-creator，以及 `skills/synced` 里的，都跟着 claude.ai 账号走，登录就有。

本机的 skill 或 agent 有增减时，在仓库目录里跑一下再提交：

```bash
rsync -a --delete --exclude synced --exclude learned --exclude .DS_Store ~/.claude/skills/ skills/
```

```bash
rsync -a --delete --exclude .DS_Store ~/.claude/agents/ agents/
```

## 一、换电脑（还用 Claude Code）

1. 装插件（每行分开跑）：

   ```bash
   claude plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode.git
   claude plugin marketplace add https://github.com/Leonxlnx/taste-skill.git
   claude plugin marketplace add DietrichGebert/ponytail
   claude plugin marketplace add https://github.com/affaan-m/everything-claude-code.git
   claude plugin install oh-my-claudecode@omc
   claude plugin install taste-skill@taste-skill
   claude plugin install ponytail@ponytail
   claude plugin install ecc@ecc
   claude plugin disable ecc@ecc
   ```

   OMC 的插件来源默认跟着 GitHub 的 main 分支走，main 上可能是没正式发布的版本（2026-11 的 5.8.6 就缺了 `bridge/*.cjs` 和 `dist/`，见 [#5027](https://github.com/Yeachan-Heo/oh-my-claudecode/issues/5027)）。所以固定到正式发布的版本：在 `~/.claude/settings.json` 的 `extraKnownMarketplaces.omc.source` 里加 `"ref": "v5.8.4"`（`~/.claude/plugins/known_marketplaces.json` 里同一项也加），再跑 `claude plugin marketplace update omc`，然后卸载重装 OMC。以后要升级，先到 [Releases](https://github.com/Yeachan-Heo/oh-my-claudecode/releases) 确认新版本已经正式发布，再改这个 `ref`。

2. 在 Claude Code 里跑一次 `/oh-my-claudecode:omc-setup`，它会写好全局 `CLAUDE.md` 和 HUD 状态栏。
3. `~/.claude/settings.json` 里补两项：`"effortLevel": "high"`，`"env": { "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1" }`（OMC 的 team 功能要用）。
4. 拷 skill 和 agent（在本仓库目录里跑）：

   ```bash
   mkdir -p ~/.claude/skills && cp -R skills/. ~/.claude/skills/
   ```

   ```bash
   mkdir -p ~/.claude/agents && cp agents/*.md ~/.claude/agents/
   ```

## 二、换成 Codex

- **自己的 skill**：SKILL.md 格式是通用的，把本仓库 `skills/` 下的 19 个文件夹拷到 `~/.codex/skills/` 就能用。
- **ponytail**：有 Codex 版，直接装。
- **ECC**：有官方 Codex 版，可以直接装。常用的 5 个 skill 已经跟着第一条拷过去了，所以一般不用装整个 ECC。
- **taste-skill**：2.5 本身是一个 SKILL.md 加脚本，把上游仓库 `skills/` 下的文件夹拷进 `~/.codex/skills/` 就能用。minimalist-ui、redesign-existing-projects 已在本仓库 `skills/` 里，跟第一条一起拷过去。
- **OMC**：只能在 Claude Code 里用。同一个作者做了 Codex 版 [oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex)（OmX），功能类似（钩子、agent 团队、HUD），但是另一个项目，得重新配。
- **全局规则**：Codex 读的是 `~/.codex/AGENTS.md`。`~/.claude/CLAUDE.md` 里 OMC 那一大段是给 Claude Code 编排 agent 用的，不要照搬，只挑通用的偏好写进去，比如用中文交流。
- **自动模式规则、状态栏、ECC 钩子**：Codex 没有对应的东西，不迁。

在本仓库目录里跑：

```bash
mkdir -p ~/.codex/skills && cp -R skills/. ~/.codex/skills/
git clone https://github.com/Leonxlnx/taste-skill /tmp/taste-skill
for d in /tmp/taste-skill/skills/*/; do cp -R "${d%/}" ~/.codex/skills/; done
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
