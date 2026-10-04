# 第 4 级：讲解视频（3b1b 风格）

## 什么时候用

内容的核心是一个**随时间展开的过程**：一步步的推导、一个形状怎么变成另一个形状、一个点怎么沿曲面移动。网页能让读者自己拖，视频能让读者跟着一条精心安排的路线看，同时听旁白。

视频最贵：要写分镜、要渲染、要配音，改一处就要重新渲染。先确认第 1–3 级讲不清，再做视频。

## 本 skill 做什么、不做什么

- **做：** 写分镜脚本，写旁白，推荐工具链，给出交给工具的 prompt。
- **不做：** 本 skill 不自己渲染视频，也不自己装工具。用户装好工具后，把分镜交给工具执行。

## 第一步：先写文字稿

按 `plain-chinese` 写完整的文字稿，并让用户确认内容正确。视频里的错误比文字里的错误更有说服力，所以审稿要放在渲染之前。

## 第二步：写分镜

用表格写，每行一个镜头：

| 镜头 | 时长 | 画面 | 旁白 |
|---|---|---|---|
| 1 | 5 秒 | 标题卡：「梯度下降为什么会往下走」 | 这段视频讲一件事：梯度下降怎么找到最低点。 |
| 2 | 10 秒 | 一个碗形曲面，一个小球停在碗壁上 | 把损失函数想成一个碗。我们要找碗底。 |
| 3 | 12 秒 | 小球位置画出一个箭头，指向最陡的上坡方向 | 梯度指向最陡的上坡方向。 |
| … | … | … | … |
| 末 | 6 秒 | 回顾卡：3 句要点 | 回顾一下…… |

规则：

1. 一个镜头只讲一件事。旁白按 `plain-chinese` 写，每句不超过 25 字。
2. 画面先动，旁白后说；或者画面和旁白同时出现。不要让旁白先讲到画面还没出现的东西。
3. 开头用标题卡说「这段要讲什么」，结尾用回顾卡总结。
4. 总长先按 60–120 秒设计。旁白语速按每分钟约 200 字估算。
5. 公式出现时，用颜色把公式里的符号和画面里的对象对应起来。

## 第三步：选工具链

| 需求 | 工具 | 说明 |
|---|---|---|
| 让 coding agent 一条龙生成视频 | [showtime](https://github.com/FavioVazquez/showtime) | 开源，本地渲染，不需要 API key。0.3 版，作者自述仍属早期。Claude Code 里用 `/plugin marketplace add FavioVazquez/showtime` 安装 |
| 自己控制数学动画 | [Manim Community](https://www.manim.community/) | 3Blue1Brown 风格动画的开源库，用 Python 写场景 |
| 免费本地配音 | [Kokoro](https://github.com/hexgrad/kokoro)（ONNX 版：[kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx)） | 本地 TTS，无需联网。中文音色先试听再用 |
| 付费高质量配音 | [ElevenLabs](https://elevenlabs.io/) | 需要 API key |
| 合成视频、加字幕 | [ffmpeg](https://ffmpeg.org/) | 合并画面、音频和字幕 |

Karpathy 原帖的做法是：「Create a 3b1b style video explainer on X」，旁白用 ElevenLabs。帖子评论区有人用 Manim + 本地 Kokoro 跑通了免费路线。

工具版本变化快。推荐前先打开链接，确认安装方式没变。

## 第四步：交付

交给用户：

1. 文字稿（已确认）。
2. 分镜表。
3. 一段可以直接交给视频工具的 prompt，例如：

> Create a 3b1b style video explainer on gradient descent, about 90 seconds. Follow this storyboard exactly: [粘贴分镜表]. Narration in Chinese, use a free local TTS voice. Burn in captions.

4. 「需要核对」：哪些画面是示意，不是真实数据；公式和数字要在渲染前核对。

## 没有视频工具时

退回第 3 级：把分镜做成一个 HTML 页面，每个镜头一张卡片，点「下一步」播放 CSS/SVG 动画，并显示旁白字幕。读者得到的体验接近视频，成本低很多。
