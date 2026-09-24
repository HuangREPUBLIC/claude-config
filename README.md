# 从 Claude Code 换到 Codex

同一台电脑上换成 Codex 时照这个做。只记「装了什么、从哪装」，不放本机文件。

更新于 2026-09-25。

## 逐项怎么迁

- **自己的 skill**：SKILL.md 格式是通用的，把 `~/.claude/skills/` 下的 13 个文件夹（`synced`、`learned` 除外）拷到 `~/.codex/skills/` 就能用。
  来源：7 个动画/设计 skill 来自 [emilkowalski/skills](https://github.com/emilkowalski/skills)；design-md 照 [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) 整理；另外 5 个（make-interfaces-feel-better、frontend-design-direction、accessibility、strategic-compact、liquid-glass-design）是从 ECC 里拷出来的。
- **superpowers**：有官方 Codex 版，直接装。
- **ponytail**：有 Codex 版，直接装。
- **ECC**（[affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)）：有官方 Codex 版，可以直接装。在 Claude Code 里是停用的（284 个 skill 加一大堆钩子，太重），常用的 5 个 skill 已经在上面第一条里跟着拷过去了，所以 Codex 上一般不用装整个 ECC。
- **taste-skill**：没有 Codex 插件包，但它本身就是一堆 SKILL.md，把 [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) 的 `skills/` 下的文件夹拷进 `~/.codex/skills/` 就能用。
- **OMC**：只能在 Claude Code 里用。同一个作者做了 Codex 版 [oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex)（OmX），功能类似（钩子、agent 团队、HUD），但是另一个项目，得重新配。
- **swift-lsp**：Claude Code 专用，不用迁。
- **全局规则**：Codex 读的是 `~/.codex/AGENTS.md`。`~/.claude/CLAUDE.md` 里 OMC 那一大段是给 Claude Code 编排 agent 用的，不要照搬，只挑通用的偏好写进去，比如用中文交流。
- **自动模式规则、状态栏、ECC 钩子**：Codex 没有对应的东西，不迁。

## 命令

```bash
mkdir -p ~/.codex/skills
for d in ~/.claude/skills/*/; do case "$d" in */synced/|*/learned/) ;; *) cp -R "${d%/}" ~/.codex/skills/ ;; esac; done
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
