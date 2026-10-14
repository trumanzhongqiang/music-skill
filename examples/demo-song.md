# 演示：一句情绪到一支 MV 提示词

> ⚠️ 本示例的词曲与画面**完全虚构**，仅用于演示 music-skill 的工作方式与产出格式。
> 演示链路：情绪输入 → 情绪内核 → 歌词片段 → 曲风提示词 → 单个分镜的首尾帧/视频提示词。

输入：

> 启动原创音乐：夏夜雨后一个人散步的释然

---

## 1. 情绪内核（阶段 0 锚定，所有后续阶段共用）

```markdown
# 情绪内核

- 情绪对：释然 × 一丝怅惘
- 核心意象：雨后的路灯 / 湿漉漉的街面反光 / 拖着长影子的人
- 能量曲线：平静（主歌）→ 抬升（预副歌）→ 舒展爆发（副歌）→ 回落（尾段）
- 风格锚定句：90 年代华语抒情流行，深夜电台质感
```

**Skill 在做什么**：先把模糊情绪落成四个可检查的字段。后续歌词的意象、曲风的配器、MV 的色调，都必须能指回这张锚——这是「歌词在下雨、曲风在燃」这种各说各话的防线。

## 2. 歌词片段（阶段 1，节选副歌）

```markdown
[副歌]
雨停了 路灯把影子拉长
积水里 晃着半边月亮
我走得很慢 也不用赶
有些事放下了 就不算遗憾
```

**自检可见**：句句押韵（ang 韵）、每句一个可感知画面（路灯、积水、月亮）、比主歌短狠好记、意象全部来自情绪内核。

## 3. 曲风提示词（阶段 2，可直接粘贴进 Suno）

```
mandopop ballad, 90s taipei late-night radio, 72-78 bpm, 4/4,
felt piano intro, warm pad strings entering at verse 2, soft drums
and bass at second chorus, intimate breathy female vocal, emotional
build from restrained verse to open soaring chorus
```

**五要素齐全**：流派（mandopop ballad）、年代参照（90s taipei）、节奏（72-78 bpm, 4/4）、配器（钢琴→弦乐→鼓贝斯逐步进入）、人声与情绪曲线（气声女声，主歌克制→副歌舒展）——与阶段 0 的能量曲线一致。

## 4. 一个分镜的提示词（阶段 4/5/6，节选镜头 12）

分镜表条目：

| 镜头 | 景别 | 运镜 | 画面 | 时长 | 对应歌词 |
|------|------|------|------|------|----------|
| 12 | 全景 | 缓慢前推 | 雨后街道，路灯下人物背影，影子被拉长 | 4s | 「雨停了 路灯把影子拉长」 |

首帧提示词（图生视频用）：

```
a person standing still under a warm street lamp on a wet street after
rain at night, long shadow stretching forward, teal-grey tones with warm
lamp glow, film grain, wide shot, 35mm feel
```

尾帧提示词——**与首帧只差动作发展**：

```
a person beginning to walk away from a warm street lamp on a wet street
after rain at night, long shadow stretching forward, teal-grey tones with
warm lamp glow, film grain, wide shot, 35mm feel
```

视频提示词：

```
[首帧] + [尾帧] + 镜头缓慢前推，人物从静止转为缓步走开，影子随步伐轻晃
```

**纪律可见**：首帧与尾帧之间，主体、场景、光线、色调、风格后缀逐字一致，唯一差异是「动作发展」——这是图生视频不跳变、人物不闪烁的关键。

---

以上每个阶段的产物都可单独使用；全链路交付与质检四查详见 [`skill/music-skill/SKILL.md`](../skill/music-skill/SKILL.md) 与 [`references/quality-checklist.md`](../skill/music-skill/references/quality-checklist.md)。
