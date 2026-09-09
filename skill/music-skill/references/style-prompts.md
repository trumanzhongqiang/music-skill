# 曲风提示词模板（Suno 类音乐生成模型）

本文档提供曲风提示词（style prompt）的结构规范、常用流派模板和歌词自检清单。阶段 2 产出曲风提示词时使用。

## 一、Style Prompt 五要素结构

一段合格的曲风提示词必须包含以下五部分，缺一不可：

```
[流派], [年代/地域参照], [BPM 与拍号], [配器], [人声与情绪曲线]
```

- **流派**：1~2 个标签，宁精勿杂。`indie folk` 好，`pop rock electronic folk` 坏。
- **年代/地域参照**：给模型一个声音锚，如 `90s taipei`、`early 2000s tokyo`、`1970s laurel canyon`。
- **BPM 与拍号**：写范围比写死好，如 `72 bpm, 4/4`。情绪曲线靠配器和编曲推进，不靠 BPM 突变。
- **配器**：4~6 件核心乐器，标注进入时机（见下方能量曲线）。
- **人声与情绪曲线**：声线质感 + 各段落能量标注。

## 二、常用流派模板

### 1. 抒情流行（Mandopop Ballad）

```
mandopop ballad, 90s taipei late-night radio, 70-78 bpm, 4/4,
felt piano intro, warm pad strings entering at verse 2, soft drums and
bass at second chorus, electric guitar arpeggio after bridge,
intimate breathy female vocal, emotional build from restrained verse to
soaring final chorus
```

适用情绪：释然、思念、心碎但倔强、深夜独白。

### 2. 独立民谣（Indie Folk）

```
indie folk, 2010s bandcamp bedroom recording, 82-90 bpm, 4/4,
fingerpicked acoustic guitar, muted brushed drums, subtle cello line,
group harmonies on chorus, dry close-miked male vocal, warm and
slightly lo-fi, gentle swaying dynamics
```

适用情绪：散步、季节感、平淡日常里的小确丧、温柔叙事。

### 3. 摇滚（Rock）

```
alternative rock, 2000s garage revival, 128-140 bpm, 4/4,
overdriven power chords, driving eighth-note bass, crashing cymbals,
quiet-loud dynamics, raw slightly-shouted vocal with gang vocals on
chorus, anthemic and cathartic
```

适用情绪：爆发、不服、燃烧、和解前的挣扎。

### 4. 电子（Electronic）

```
chill electronic, late night city drive, 95-105 bpm, 4/4,
pulsing synth bass, glassy pluck arpeggios, sidechained pads, minimal
trap-influenced beat at chorus, airy processed vocal with vocoder
harmonies, neon-lit nocturnal mood
```

适用情绪：都市孤独、雨夜、未来感、克制的躁动。

### 5. R&B / 嘻哈（R&B / Hip-hop）

```
contemporary r&b, slow jam, 68-76 bpm, 4/4,
deep sub bass, sparse rhodes chords, snapping rimshot beat,
808 slides in verse 2, smooth melismatic vocal with stacked harmonies,
confident but wounded
```

适用情绪：慵懒、欲言又止、自尊与脆弱并存。

## 三、情绪曲线标注规范

在 style prompt 末尾用一句话标注能量走向，与阶段 0 的能量曲线对齐：

```
energy: minimal intro → restrained verse → lift at pre-chorus →
full-band cathartic chorus → stripped bridge → biggest final chorus
```

常见曲线模式：

- **渐强型**：`restrained → building → cathartic`（释怀、燃）
- **起伏型**：`soft verse → big chorus → quiet bridge → huge outro`（情歌标配）
- **平流型**：`steady mid-energy with subtle swells`（民谣、lo-fi，情绪靠细节不靠爆发）

## 四、歌词自检清单（阶段 1 交付前逐条过）

1. 整首一个韵脚，副歌句句押韵
2. 每段开头两行内出现一个核心意象
3. 删掉所有抽象词，换成看得见的画面（「很难过」→「把伞倾向你那一边」）
4. 副歌任意一句单独拎出来，路人能看懂这首歌在唱什么
5. 桥段必须和主歌视角不同（时间、人称、空间至少换一个）
6. 念出来不顺口的句子，改到顺口为止

## 五、常见错误

- 流派标签超过 3 个 → 模型产出四不像
- 只写情绪不写乐器 → 编曲随机，副歌推不起来
- 给 BPM 写死一个值 → 失去弹性；写范围，如 `100-108 bpm`
- 中英文混排在同一段 prompt 里 → Suno 类模型对英文 style prompt 响应更稳定，歌词再单独给中文
