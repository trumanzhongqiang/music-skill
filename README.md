# 原创音乐 music-skill 🎵

![version](https://img.shields.io/badge/version-1.3.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![platform](https://img.shields.io/badge/platform-WorkBuddy-orange)

> 从一句情绪到一首完整的歌：AI 一条龙生成歌词、曲风提示词、MV 概念、分镜脚本、首尾帧与视频提示词。
>
> From a single emotion to a complete song: an AI pipeline generating lyrics, Suno-style prompts, MV concepts, storyboards, and first/last-frame video prompts. [English README](#english-readme)

音乐创作不该只属于专业音乐人。普通人说不清「BPM 和调式」，但说得出「心碎但倔强」。这个 Skill 接收一句情绪描述，自动走完一条完整的 AI 音乐创作链路：歌词 → 曲风 → MV → 分镜 → 视频提示词，每一步的产出都可以直接粘贴进对应的生成工具（Suno、图生视频、视频生成模型）。

## 核心优势

与同类项目的区别在于——多数同类 Skill 到「歌词 + Suno 提示词」就结束了，这个 Skill 一直走到**视频生成模型的提示词**：

1. **覆盖 MV 全链路**：情绪 → 歌词 → 曲风 → MV 概念 → 逐镜头分镜 → 首尾帧图像提示词 → 视频提示词，可直接对接图生视频/视频生成工具
2. **跨阶段一致性机制**：所有阶段共享同一份「情绪内核」（情绪对/核心意象/能量曲线/锚定句），质检第一查专门核对各阶段是否偏离锚点
3. **首尾帧一致性纪律**：针对图生视频的帧间跳变问题，强制首帧与尾帧只差「动作发展」，风格后缀全片逐字复用，质检中用逐字 diff 审计
4. **质检四查可判定**：情绪锚定/提示词可执行/文字清晰/节奏，每条都写明「什么样算过、什么样算不过」
5. **中文创作专项**：内置中文韵脚库（开口韵/闭口韵选型、副歌 Hook 写法），押韵纪律精确到「副歌句句押、主歌可松散」

## 功能特性

- **情绪是起点**：只需描述一种情绪或一个故事（如「夏夜雨后一个人散步的释然」），无需任何音乐术语
- **一条龙但可分步**：可以一键跑完全程，也可以只生成歌词、只设计 MV，随取随用，各阶段产物自包含
- **歌词创作**：基于情绪意象写作，控制押韵与结构（主歌/副歌/桥段），副歌句句押韵、短狠好记
- **曲风提示词**：为 Suno 类音乐生成模型设计风格 Prompt（流派、节奏、配器、人声、情绪曲线五要素 + 排除风格），附 16 套常用流派模板（含情绪速查表）
- **MV 概念设计**：整体视觉风格、色调、叙事主线、场景清单
- **分镜脚本**：逐镜头的画面描述、景别、运镜、时长，附分镜表模板
- **首尾帧提示词**：为每个分镜生成首帧/尾帧图像提示词，首尾帧只差「动作发展」，保证视频连贯
- **视频提示词**：首尾帧 + 运动描述，交给视频生成模型产出最终分镜片段
- **风格一致性**：歌词意象、曲风、MV 视觉共享同一份「情绪内核」，避免各说各话
- **演唱设计**：男声/女声独唱、男女对唱、合唱分配，标注合唱高潮位置
- **发音校正**：交付前扫描多音字、阿拉伯数字、生僻英文，预防 Suno 唱错字
- **可选端到端生成**：本地装有 Suno CLI 等生成工具时，确认额度消耗后可直接生成音频/LRC 与分镜视频素材，从一句情绪到成品文件一条命令走完

## 快速开始

**WorkBuddy 用户：**

1. 下载本仓库的 [`music-skill.skill`](./music-skill.skill) 文件
2. 在 WorkBuddy 中加载该 `.skill` 文件
3. 说「启动原创音乐」+ 一句情绪描述，例如：

   > 启动原创音乐：夏夜雨后一个人散步的释然

也可以只调用其中一环：

> 帮我写首歌词：心碎但倔强，不要苦情，要有骨气

**其他支持 SKILL.md 规范的助手：** 直接让助手读取 [`skill/music-skill/SKILL.md`](./skill/music-skill/SKILL.md) 并按其中的指令工作即可。

## 演示示例

想看看实际产出长什么样？[`examples/demo-song.md`](./examples/demo-song.md) 里有一份完整的虚构演示：从一句「夏夜雨后一个人散步的释然」出发，展示情绪内核、歌词副歌、Suno 曲风提示词和一个分镜的首尾帧/视频提示词。

## 工作方式

```
情绪描述
  → 情绪解析与风格锚定（情绪对 / 核心意象 / 能量曲线 / 风格锚定句）
  → 歌词（主歌/副歌/桥段，押韵与意象纪律，演唱形式设计）
  → 曲风提示词（Suno 类模型，五要素 + 排除风格）
  → 发音校正（多音字/数字/英文，防 Suno 唱错）
  → MV 概念（视觉风格 / 叙事主线 / 场景清单）
  → 分镜脚本（逐镜头：景别 / 运镜 / 时长）
  → 首尾帧提示词（图生视频模型）
  → 视频提示词（视频生成模型）
  → 可选：调用本地生成工具直接产出音频与视频素材
```

交付时按目录组织，各阶段产物自包含，可单独使用：

```
song-标题/
├── 00-情绪内核.md
├── 01-歌词.md
├── 02-曲风提示词.md
├── 03-MV概念.md
├── 04-分镜脚本.md        # 含全部镜头的首尾帧与视频提示词
└── 05-生成清单.md        # 可直接粘贴进生成工具的提示词全集
```

## 质量保证

交付前必须逐项通过「质检四查」（[`skill/music-skill/references/quality-checklist.md`](./skill/music-skill/references/quality-checklist.md)），任一查不过就回对应阶段重改：

1. **情绪锚定**：歌词、曲风、MV 是否共用同一份情绪内核，还是各说各话
2. **提示词可执行**：曲风五要素齐全、首尾帧只差动作、相邻镜头景别运别有变化
3. **文字清晰**：歌词无抽象抒情句，副歌句句押韵
4. **节奏**：能量曲线贯穿歌词结构、配器推进与分镜节奏

## 目录结构

```
music-skill/
├── README.md                        # 本文件
├── LICENSE                          # MIT License
├── SKILL.md                         # 根级 Skill 说明（WorkBuddy 规范 frontmatter）
├── music-skill.skill                # 打包文件（WorkBuddy 直接加载）
├── examples/
│   └── demo-song.md                 # 虚构演示：情绪 → 歌词 → 曲风 → 分镜提示词
├── tests/
│   └── test-cases.md                # 实测案例集（翻车点写回 SKILL.md 红线）
└── skill/
    └── music-skill/
        ├── SKILL.md                 # 核心执行指令（AI 的工作流）
        └── references/
            ├── rhyme-library.md         # 中文韵脚库（选韵总则 + 韵脚表 + Hook 写法）
            ├── suno-pronunciation.md    # Suno 中文发音指南（多音字/数字/英文避坑）
            ├── style-prompts.md         # 曲风提示词模板（五要素 + 排除风格 + 16 套流派模板）
            ├── storyboard-templates.md  # 分镜表模板 + 首尾帧/视频提示词写法
            └── quality-checklist.md     # 质检四查（情绪锚定/可执行/文字/节奏）
```

## 与生成工具的关系

本 Skill 只产出创作素材与提示词，不直接生成音视频。产出格式（歌词文件 + style tags + exclude styles）兼容主流 Suno CLI 工作流，可直接交接给生成类工具（如 [qiaomu-suno-master](https://github.com/joeseesun/qiaomu-suno-master)）完成真实生成与下载。

## 常见问题

**Q：Skill 会直接生成音频或视频文件吗？**
默认不生成，只产出可直接粘贴到 Suno、图生视频、视频生成工具里的提示词和文档。如果你本地装了 Suno CLI 等生成工具，它也可以在你确认额度消耗后直接执行生成，把音频/LRC 和分镜视频素材落到本地。

**Q：没有音乐基础能用吗？**
这正是它的设计目标。你只需要描述情绪和故事，专业部分（结构、押韵、BPM、运镜）由 Skill 处理，每个决策都会给你一句能看懂的理由。

**Q：能模仿某位歌手的风格吗？**
不点名模仿在世歌手（涉及侵权与平台下架风险），但可以精确到流派与年代参照，如「90 年代华语抒情流行，深夜电台质感」。

## License

[MIT](LICENSE) © 2026 Zhongqiang Wang

---

## English README

**music-skill** turns one sentence of emotion into a complete song package — lyrics, a Suno-ready style prompt, an MV concept, a shot-by-shot storyboard, and first/last-frame video prompts.

### How it works

1. Load `music-skill.skill` in WorkBuddy (or point any AI assistant at `skill/music-skill/SKILL.md`)
2. Say "启动原创音乐" plus an emotion or story, e.g. "夏夜雨后一个人散步的释然" (the relief of a solo walk after summer rain)
3. The AI first distills an **emotional core** (emotion pair, 2–3 visualizable images, energy curve, one-line style anchor) that every later stage must cite — this is what keeps lyrics, music, and visuals from drifting apart
4. Each stage's output is paste-ready: lyrics with structure tags and vocal arrangement, a five-element Suno style prompt with exclude styles, an MV concept, a 30–50 shot storyboard, and first/last-frame + motion prompts for video generation models. Optionally, if a local Suno CLI is installed, it can execute generation end-to-end after confirming credit usage — from one emotion line to actual audio/LRC and video clip files
5. You can also invoke any single stage ("帮我写首歌词…") — every artifact is self-contained

### Key properties

- **Consistency by construction**: lyrics, style, and visuals all share the same emotional core
- **Paste-ready prompts**: five-element style prompts; first/last frames differ only in motion, so img2video stays coherent
- **Quality gate**: a four-point checklist (emotional anchoring / prompt executability / prose clarity / pacing) must pass before delivery
- **Chinese songwriting focus**: built-in rhyme library (open/closed vowel selection, chorus hook patterns) with strict rhyming discipline — every chorus line must rhyme
- **No impersonation**: genres and era references only — never named living artists

See `examples/demo-song.md` for a full (fictional) demo from one emotion line to prompts.

License: [MIT](LICENSE) © 2026 Zhongqiang Wang
