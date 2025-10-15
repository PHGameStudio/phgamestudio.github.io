---
layout: default
title: Rules Guide
permalink: /resources/rules-guide/
toc: true
---

# Rules Guide

### Quick setup for Windsurf Cascade rules · 速览 Windsurf Cascade 规则
For rules setup, guides to "__Rules, Memories & Workflows__" at right up of __cascade chat box__(usually set in right of IDE, with a windsurf icon and name "Cascade code/chat")

Then add either __Global rules__ or __Workspace__

### Recommended Rules · 推荐规则

#### Coding Related Rules · 编码相关规约

1. **Use consistent indentation.** Default to tabs; if the language does not support tabs, use 4 spaces. When only one indentation style exists, follow that style.  

- **使用一致的缩进。** 默认使用制表符；若语言不支持制表符，则使用 4 个空格。若语言仅支持一种缩进方式，请遵循该方式。

#### Download Related Rules · 下载相关规约

1. **Prefer package managers.** When configuring the development environment, prioritize installing dependencies via system package managers (winget on Windows, Homebrew on macOS, system package manager or Homebrew on Linux). If unavailable, prefer language-specific managers (e.g., pip, cargo) over direct binary downloads.  

- **优先使用包管理器。** 设置开发环境时，应优先通过系统包管理器（Windows 使用 winget、macOS 使用 Homebrew、Linux 使用系统包管理器或 Homebrew）安装依赖；若不可用，请优先使用语言专属包管理器（如 pip、cargo），而不是直接下载二进制文件。

#### Cascade and Project Management Rules · Cascade 与项目管理规约

1. **Deliver only the requested scope per round.** Even when a todo list includes items A, B, and C, if the user asks for “task A,” do not complete tasks B and C in that round.  

- **每轮只完成本次请求范围。** 即使待办列表包含 A、B、C，当用户仅要求“执行任务 A”时，不要在同一轮中继续完成 B 和 C。

2. **Restate the user request before acting.** Confirm understanding by repeating each instruction verbatim prior to execution.  

- **行动前复述用户请求。** 在执行前逐条复述用户指令，以确认理解无误。

3. **Ask for permission before executing.** Get user's permission when required to change projects.