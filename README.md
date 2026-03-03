# MacTermConfig

macOS 终端美化配置，通过 Claude Code Skill 一键引导完成 iTerm2 + zsh 现代化终端环境搭建。

## 效果预览

执行 Skill 后，你的终端将拥有：

- **简洁的命令提示符** — Starship，只显示当前目录路径，无多余噪音
- **彩色文件列表** — `ls` / `ll` 带图标、颜色分类、Git 状态标注
- **Dracula 配色** — 护眼深色主题，代码与输出层次分明
- **输入智能补全** — 灰色历史命令提示，按 → 键接受；Tab 补全大小写不敏感
- **语法高亮** — 命令输入时实时着色，错误命令立刻变红
- **Vim 增强** — 行号、语法高亮、缩进规则、游标行高亮

## 包含组件

| 组件 | 用途 |
|------|------|
| [Starship](https://starship.rs) | 跨 shell 的极简命令提示符 |
| [eza](https://eza.rocks) | 现代 `ls` 替代，支持图标与颜色 |
| JetBrainsMonoNL Nerd Font | 支持图标显示的等宽字体 |
| Dracula | iTerm2 颜色主题 |
| zsh-autosuggestions | 历史命令灰色补全提示 |
| zsh-syntax-highlighting | 命令行实时语法高亮 |
| zstyle completion | Tab 补全大小写不敏感 |
| Vim config | 编辑器基础增强配置 |

**前置要求：** macOS + iTerm2 + Homebrew

## 如何使用

### 方式一：用 Claude Code 执行 Skill（推荐）

1. 将本仓库的 skill 文件复制到 Claude Code skills 目录：

   ```bash
   mkdir -p ~/.claude/skills/mac-iterm-setup
   cp mac-iterm-setup/SKILL.md ~/.claude/skills/mac-iterm-setup/SKILL.md
   ```

2. 打开 Claude Code，直接说：

   ```
   帮我配置终端环境
   ```
   或
   ```
   beautify my terminal
   ```

   Claude 会自动识别并加载 `mac-iterm-setup` skill，逐步引导你完成安装与配置，并在每一步检查是否已存在，避免重复操作。

### 方式二：手动参照 Skill 文档

直接阅读 [mac-iterm-setup/SKILL.md](mac-iterm-setup/SKILL.md)，按各章节顺序手动执行命令。

## 目录结构

```
MacTermConfig/
├── mac-iterm-setup/
│   └── SKILL.md      # Claude Code skill，包含完整安装步骤
├── CLAUDE.md          # Claude Code 项目配置
└── README.md
```
