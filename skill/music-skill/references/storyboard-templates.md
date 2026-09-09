# 分镜表与首尾帧/视频提示词模板

本文档提供 MV 分镜表的字段规范、填写示例，以及首尾帧图像提示词、视频提示词的写法规则。阶段 4~6 使用。

## 一、分镜表字段

| 字段 | 说明 |
|------|------|
| 镜头号 | 三位数连续编号，跨场景也连续（001、002…），方便后期检索 |
| 场景 | 所属场景名，与 MV 概念的场景清单对应 |
| 段落 | 对应歌词段落（主歌 1 / 副歌 / 桥段…），决定镜头节奏 |
| 景别 | 远景 / 全景 / 中景 / 近景 / 特写 |
| 运镜 | 固定 / 推 / 拉 / 摇 / 移 / 跟 / 手持晃动 |
| 时长 | 2~5 秒，副歌段偏短，主歌段偏长 |
| 画面描述 | 一句话说清主体、动作、环境、光线 |
| 首帧提示词 | 给图生视频模型的起始帧图像提示词 |
| 尾帧提示词 | 结束帧图像提示词（与首帧只差动作发展） |
| 视频提示词 | 首帧 + 尾帧 + 运动描述，给视频生成模型 |

## 二、分镜表示例（3 个镜头节选）

| 镜头号 | 场景 | 段落 | 景别 | 运镜 | 时长 | 画面描述 |
|--------|------|------|------|------|------|----------|
| 001 | 雨夜街道 | 前奏 | 远景 | 固定 | 4s | 空荡的十字路口，路灯把积水染成暖黄，远处一个人影撑伞走过 |
| 012 | 雨夜街道 | 副歌 | 中景 | 缓慢前推 | 3s | 人物走到路灯下停住，抬头，雨丝在光里发亮 |
| 013 | 雨夜街道 | 副歌 | 特写 | 固定 | 3s | 人物侧脸，水珠顺着下颌线滴落，表情释然 |

镜头衔接纪律：相邻镜头不要同景别 + 同运镜；副歌段相邻镜头时长差异不要超过 1 秒。

## 三、首帧/尾帧提示词写法

每帧提示词固定五段式：

```
[主体与动作] + [环境] + [光线] + [色调与质感] + [镜头参数]
```

示例（镜头 012 首帧）：

```
a person in a light coat holding a transparent umbrella, walking toward
a streetlamp on a rain-wet crossroad at night, warm sodium lamp glow
reflecting on puddles, teal-grey city with amber highlights, cinematic
film grain, medium shot, 35mm look
```

同一镜头的尾帧只改动作发展，其余逐字复用：

```
a person in a light coat standing still under a streetlamp, umbrella
lowered, looking up, rain-wet crossroad at night, warm sodium lamp glow
reflecting on puddles, teal-grey city with amber highlights, cinematic
film grain, medium shot, 35mm look
```

规则：

- 首尾帧的主体、服装、场景、光线、色调、镜头参数**必须完全一致**
- 全片统一风格后缀（本例为 `teal-grey city with amber highlights, cinematic film grain`），每个镜头原样复用，保证跨镜头一致性
- 禁写抽象词（「悲伤的氛围」），全部落成可拍摄元素（姿态、光线、道具）
- 人写具体外观（年龄感、服装颜色、发型），跨镜头保持同一描述

## 四、视频提示词写法

```
首帧提示词
→ 尾帧提示词
→ motion: [主体动作] + [镜头运动]，一句话
```

示例（镜头 012）：

```
motion: camera slowly pushes in as the person stops walking, lowers the
umbrella and looks up, raindrops glinting in the lamplight
```

规则：

- 运动描述不超过一句话，只写「谁动了、怎么动、镜头怎么动」
- 运镜方式必须与分镜表「运镜」字段一致（表写推，这里就写 push in）
- 时长以分镜表为准，不写进提示词，在生成工具里设置

## 五、交付清单格式

阶段 6 完成后，按此清单交付，方便用户逐个复制到生成工具：

```
镜头 001：图像提示词 × 2（首帧/尾帧），视频提示词 × 1
镜头 002：图像提示词 × 2（首帧/尾帧），视频提示词 × 1
…
Suno style prompt × 1，歌词（带结构标注）× 1
```
