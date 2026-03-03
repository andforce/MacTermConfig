# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository stores macOS terminal environment configuration files for iTerm2 + zsh setup, targeting Android development workflows.

## Tech Stack

- **Terminal:** iTerm2
- **Shell:** zsh
- **Prompt:** Starship (`~/.config/starship.toml`)
- **File listing:** eza (replaces `ls`)
- **Font:** JetBrainsMonoNL Nerd Font Mono
- **Color theme:** Dracula
- **zsh plugins:** zsh-autosuggestions, zsh-syntax-highlighting
- **Editor config:** Vim (`~/.vimrc`)

## Skill

The `mac-iterm-setup` skill at `~/.claude/skills/mac-iterm-setup/SKILL.md` covers the full setup procedure. Use it when configuring or troubleshooting the terminal environment.

## Environment Context

The user's `~/.zshrc` includes: Conda, SDKMAN, Android SDK, JAVA_HOME (Azul JDK 11), thefuck, Kaku integration (removed), and Starship. When editing shell config, preserve the load order — `zsh-syntax-highlighting` must be sourced last.
