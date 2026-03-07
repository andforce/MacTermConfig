---
name: mac-iterm-setup
description: Use when configuring iTerm2 terminal environment on macOS - setting up Starship prompt, eza file listing, Nerd Font, Dracula color theme, zsh autosuggestions, or Vim syntax highlighting. Triggers on requests to beautify terminal, fix prompt display, configure iTerm, or install zsh plugins.
---

# Mac iTerm2 Terminal Setup

## Overview

Complete configuration guide for a modern macOS terminal using iTerm2 + zsh. Covers prompt (Starship), file listing (eza), fonts (Nerd Font), color theme (Dracula), shell plugins, and Vim.

**Prerequisite:** Homebrew must be installed.

## 操作前检查原则

每一步执行前，必须先检查是否已存在，避免重复配置：

- **brew install**：Homebrew 自带幂等性，重复执行安全，无需额外检查
- **修改 `~/.zshrc`**：先用 `grep` 检查目标内容是否已存在，已存在则跳过，不重复写入
  ```bash
  grep -q 'starship init zsh' ~/.zshrc || echo 'eval "$(starship init zsh)"' >> ~/.zshrc
  ```
- **`~/.config/starship.toml`**：先检查文件是否存在，存在则展示当前内容，询问用户是否覆盖，不要直接覆盖
- **`~/.vimrc`**：先读取当前内容，仅补充缺失的配置行，不整体替换

---

## 1. Starship Prompt

```bash
brew install starship
```

Add to `~/.zshrc` (at the bottom):

```zsh
eval "$(starship init zsh)"
```

**Minimal config** (`~/.config/starship.toml`) — shows directory only:

```toml
add_newline = false

[directory]
truncation_length = 3

[git_branch]
disabled = true

[character]
success_symbol = ""
error_symbol = ""
format = "$symbol"

[line_break]
disabled = true

[gradle]
disabled = true

[java]
disabled = true
```

---

## 2. eza（彩色 ls 替代）

```bash
brew install eza
```

Add to `~/.zshrc`:

```zsh
alias ls="eza --icons --group-directories-first"
alias ll="eza -lah --icons --group-directories-first --git"
alias la="eza -a --icons"
alias tree="eza --tree --icons"
```

> 如果图标显示为 `?`，是字体问题 → 见第 3 步安装 Nerd Font。

---

## 3. Nerd Font（图标字体）

```bash
brew install --cask font-jetbrains-mono-nerd-font
```

安装后在 iTerm2 里切换字体：

**iTerm2 → Settings → Profiles → Text → Font**

选择：`JetBrainsMonoNL Nerd Font Mono`
（NL = No Ligatures，终端推荐）

---

## 4. Dracula 颜色主题

```bash
curl -O https://raw.githubusercontent.com/dracula/iterm/master/Dracula.itermcolors
```

双击 `Dracula.itermcolors` 文件自动导入到 iTerm2，然后：

**iTerm2 → Settings → Profiles → Colors → Color Presets → Dracula**

---

## 5. zsh 插件

### 自动历史补全（灰色提示）

```bash
brew install zsh-autosuggestions
```

Add to `~/.zshrc`:

```zsh
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

### 语法高亮

```bash
brew install zsh-syntax-highlighting
```

Add to `~/.zshrc`（必须放在 autosuggestions **之后**，文件**最后一行**）：

```zsh
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

---

## 6. Vim 配置

`~/.vimrc`:

```vim
syntax on
set termguicolors
set number
set tabstop=4
set shiftwidth=4
set expandtab
set autoindent
set cursorline
colorscheme desert
```


---

## 7. 大小写不敏感 Tab 补全

默认 zsh 补全区分大小写（`cd CL<Tab>` 无法补全 `Class`）。加一行 `zstyle` 即可启用大小写不敏感匹配：

在 `~/.zshrc` 中添加（放在 starship init **之前**）：

```zsh
# Case-insensitive tab completion
zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
```

效果：`cd CL<Tab>` → 补全 `Class`，大小写任意组合均可匹配。

> `m:{a-zA-Z}={A-Za-z}` 的含义：补全时将大写字母映射到小写、小写映射到大写，双向不敏感。

---

## 推荐的 ~/.zshrc 结构顺序

```
1. conda initialize（如有）
2. 环境变量（ANDROID_HOME, JAVA_HOME, PATH 等）
3. SDKMAN（如有）
4. zstyle 补全配置（如大小写不敏感）
5. eval "$(starship init zsh)"
6. eza aliases
7. 其他 aliases
8. source zsh-autosuggestions
9. source zsh-syntax-highlighting   ← 必须最后
```

---

