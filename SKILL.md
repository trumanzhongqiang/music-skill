---
name: music-skill
description: "从情绪描述到完整歌曲：生成歌词、曲风提示词、MV概念、分镜脚本、首尾帧与视频提示词。触发词：'启动原创音乐'、'原创音乐'、相关自然语言请求。"
version: 1.1.0
allowed-tools: Bash, Read, Write, Edit
compatibility: Windows/macOS/Linux. Requires WorkBuddy.
metadata:
  emoji: "🎵"
---

# 原创音乐

一个 AI 音乐创作 Skill：接收一句情绪描述（比如「夏夜雨后一个人散步的释然」），产出一条完整的创作链路——歌词、曲风提示词、MV 概念、分镜脚本、首尾帧与视频提示词，可直接拿去 Suno 类音乐模型和图生视频/视频生成工具使用。

## 使用方式

在 WorkBuddy 中加载 `music-skill.skill` 文件，然后：

- 说「启动原创音乐」+ 一句情绪或故事描述，跑完全程
- 或者只要其中一环：「帮我写首歌词」「给这首歌设计 MV 概念」「生成分镜和视频提示词」

流程覆盖：情绪锚定 → 歌词 → 曲风提示词 → MV 概念 → 分镜 → 首尾帧 → 视频提示词，交付前跑质检四查（情绪锚定 / 提示词可执行 / 文字清晰 / 节奏）。

核心执行指令见 `skill/music-skill/SKILL.md`，曲风与分镜模板见 `skill/music-skill/references/`，交付前质检清单见 `skill/music-skill/references/quality-checklist.md`。
