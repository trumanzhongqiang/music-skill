# 曲风提示词模板（Suno 类音乐生成模型）

本文档提供曲风提示词（style prompt）的结构规范、常用流派模板和歌词自检清单。阶段 2 产出曲风提示词时使用。

## 一、Style Prompt 五要素结构

一段合格的曲风提示词必须包含以下五部分，缺一不可：

```
[流派], [年代/地域参照], [BPM 与拍号], [配器], [人声与情绪曲线]
```

外加一行排除风格（exclude styles）：

```
exclude: [不想要的方向，2~4 个]
```

- **流派**：1~2 个标签，宁精勿杂。`indie folk` 好，`pop rock electronic folk` 坏。
- **年代/地域参照**：给模型一个声音锚，如 `90s taipei`、`early 2000s tokyo`、`1970s laurel canyon`。
- **BPM 与拍号**：写范围比写死好，如 `72 bpm, 4/4`。情绪曲线靠配器和编曲推进，不靠 BPM 突变。
- **配器**：4~6 件核心乐器，标注进入时机（见下方能量曲线）。
- **人声与情绪曲线**：声线质感 + 各段落能量标注。
- **排除风格**：写「不想要什么」和写「想要什么」同等重要——不写 `auto-tune`，模型可能默认给你电音处理；不写 `trap`，鼓组可能滑向陷阱鼓。从「这类歌最忌讳的处理方式」倒推，如抒情歌排除 `edm-drop, heavy-distortion`，民谣排除 `808s, auto-tune`。

## 二、常用流派模板

**情绪速查**：

| 情绪/场景 | 推荐模板 |
|-----------|----------|
| 释然、思念、心碎但倔强 | 1 抒情流行 |
| 散步、日常小确丧、温柔叙事 | 2 独立民谣 / 8 城市民谣 |
| 爆发、不服、燃烧 | 3 摇滚 / 9 朋克 |
| 都市孤独、雨夜、未来感 | 4 电子 / 11 Lo-fi |
| 慵懒、欲言又止 | 5 R&B |
| 相思、山河、古典意象 | 6 国风 |
| 态度、吐槽、自我宣言 | 7 中文说唱 |
| 复古、暧昧、老上海 | 10 爵士 |
| 学习、陪伴、背景音 | 11 Lo-fi |
| 亲子、童趣 | 12 儿歌童谣 |
| 派对、复古舞动 | 13 复古迪斯科 |
| 史诗感、纯器乐高潮 | 14 后摇 |
| 婚礼、告白 | 15 婚礼情歌 |
| 沧桑、烟熏感 | 16 蓝调 |

### 1. 抒情流行（Mandopop Ballad）

```
mandopop ballad, 90s taipei late-night radio, 70-78 bpm, 4/4,
felt piano intro, warm pad strings entering at verse 2, soft drums and
bass at second chorus, electric guitar arpeggio after bridge,
intimate breathy female vocal, emotional build from restrained verse to
soaring final chorus
exclude: edm-drop, trap, auto-tune
```

适用情绪：释然、思念、心碎但倔强、深夜独白。

### 2. 独立民谣（Indie Folk）

```
indie folk, 2010s bandcamp bedroom recording, 82-90 bpm, 4/4,
fingerpicked acoustic guitar, muted brushed drums, subtle cello line,
group harmonies on chorus, dry close-miked male vocal, warm and
slightly lo-fi, gentle swaying dynamics
exclude: heavy-distortion, edm, auto-tune
```

适用情绪：散步、季节感、平淡日常里的小确丧、温柔叙事。

### 3. 摇滚（Rock）

```
alternative rock, 2000s garage revival, 128-140 bpm, 4/4,
overdriven power chords, driving eighth-note bass, crashing cymbals,
quiet-loud dynamics, raw slightly-shouted vocal with gang vocals on
chorus, anthemic and cathartic
exclude: acoustic-only, lofi
```

适用情绪：爆发、不服、燃烧、和解前的挣扎。

### 4. 电子（Electronic）

```
chill electronic, late night city drive, 95-105 bpm, 4/4,
pulsing synth bass, glassy pluck arpeggios, sidechained pads, minimal
trap-influenced beat at chorus, airy processed vocal with vocoder
harmonies, neon-lit nocturnal mood
exclude: live-band, folk
```

适用情绪：都市孤独、雨夜、未来感、克制的躁动。

### 5. R&B / 嘻哈（R&B / Hip-hop）

```
contemporary r&b, slow jam, 68-76 bpm, 4/4,
deep sub bass, sparse rhodes chords, snapping rimshot beat,
808 slides in verse 2, smooth melismatic vocal with stacked harmonies,
confident but wounded
exclude: distorted-guitars, punk
```

适用情绪：慵懒、欲言又止、自尊与脆弱并存。

### 6. 国风（Chinese Traditional Fusion）

```
chinese traditional fusion pop, modern guofeng, 75-85 bpm, 4/4,
guzheng and bamboo flute lead melodies, erhu counter-melody at chorus,
modern drum kit and sub bass underneath, pentatonic scale hooks,
clear ethereal female vocal with operatic ornaments on the final chorus,
elegant and wistful
exclude: trap, edm-drop, auto-tune
```

适用情绪：相思、故人、山河、古典意象入歌。

### 7. 中文说唱（Chinese Hip-hop）

```
chinese hip-hop, modern boom bap, 88-96 bpm, 4/4,
dusty sampled piano loop, punchy boom bap drums, deep 808 bass slides,
vinyl crackle texture, confident rhythmic male rap with a melodic sung
hook on chorus, streetwise and defiant
exclude: edm-drop, country
```

适用情绪：态度表达、吐槽、自我宣言、底层叙事。

### 8. 城市民谣（City Folk）

```
chinese city folk, beijing houhai bar live session, 76-84 bpm, 4/4,
strummed steel-string acoustic guitar, harmonica fills between verses,
upright bass, minimal percussion, weary warm male vocal telling a story,
slightly drunken singalong on final chorus
exclude: synth, drum-machine
```

适用情绪：漂泊、房租、深夜大排档、写给一座城市的信。

### 9. 朋克（Pop Punk）

```
pop punk, 2000s skate park energy, 160-175 bpm, 4/4,
distorted power chords, fast driving drums with double-time snare hits,
melodic shouted lead vocal, gang vocal heys on chorus, raw youthful urgency
exclude: trap, ballad
```

适用情绪：中二热血、不服气、假期结束前的最后疯狂。

### 10. 爵士（Jazz Lounge）

```
mandarin jazz ballad, smoky 1950s shanghai lounge, 65-72 bpm, 4/4 swing,
walking double bass, brushed drums, mellow piano comping, soft saxophone
solo at bridge, breathy intimate female vocal, late-night elegance
exclude: edm, heavy-drums
```

适用情绪：复古暧昧、旧时光、克制的撩拨。

### 11. Lo-fi 氛围（Lo-fi Chillhop）

```
lo-fi chillhop, rainy afternoon study session, 70-80 bpm, 4/4,
dusty rhodes loop, soft boom bap beat, vinyl crackle throughout,
muted guitar licks, wordless humming vocals, cozy and unhurried
exclude: edm-drop, aggressive-drums
```

适用情绪：学习工作背景音、一个人待着的下午、轻度 emo 自救。

### 12. 儿歌童谣（Children's Song）

```
children's song, playful singalong, 100-110 bpm, 4/4,
ukulele and glockenspiel, claps and stomps, cheerful whistling hook,
bright friendly female vocal with kids choir on chorus, sunny and simple
exclude: heavy-bass, distorted-guitars, dark-synth
```

适用情绪：亲子场景、刷牙吃饭睡觉等行为引导歌、节日儿歌。

### 13. 复古迪斯科（Retro Disco Funk）

```
retro disco funk, 1980s dance floor, 115-122 bpm, 4/4,
four-on-the-floor beat, funky slap bass, shimmering string stabs,
wah-wah guitar licks, groovy falsetto male vocal with call-and-response
chorus, glittery and carefree
exclude: ballad, metal
```

适用情绪：派对、复古怀旧、没心没肺的快乐。

### 14. 后摇器乐（Post-rock Instrumental）

```
post-rock instrumental, cinematic build, 120-130 bpm half-time feel, 4/4,
clean delay-soaked guitars, slow crescendo from sparse arpeggios to
wall-of-sound climax, explosive drums at peak, no vocals
exclude: vocals, trap
```

适用情绪：史诗感 BGM、宣传片配乐、不需要歌词的情绪高潮。

### 15. 婚礼情歌（Wedding Ballad）

```
romantic wedding ballad, modern mandopop, 68-74 bpm, 4/4,
grand piano and string quartet, gentle acoustic guitar arpeggios,
swelling orchestral finale, warm sincere male-female duet harmonizing
on the final chorus, tender and celebratory
exclude: trap, aggressive-drums
```

适用情绪：婚礼、告白、纪念日。

### 16. 蓝调（Blues）

```
chinese blues rock, smoky bar band, 80-88 bpm, 12/8 shuffle,
slide guitar licks, honky-tonk piano, harmonica fills, laid-back groove,
raspy soulful male vocal, world-weary but warm
exclude: edm, auto-tune
```

适用情绪：沧桑、自嘲式洒脱、人到中年。

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
