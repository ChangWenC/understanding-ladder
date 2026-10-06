# Rung 4: explainer video (3Blue1Brown style)

## When

The core of the content is a **process that unfolds over time**: a step-by-step derivation, one shape turning into another, a point moving across a surface. A page lets the reader explore; a video walks them along a planned path with narration.

Video is the most expensive rung: storyboard, rendering, voice, and every fix means re-rendering. Confirm that rungs 1–3 cannot do the job first.

## What this skill does and does not do

- **Does:** write the storyboard and narration, recommend a toolchain, write a prompt for those tools.
- **Does not:** render video or install tools. Once the user has the tools, hand the storyboard to them.

## Step 1: draft first

Write the full rung-1 draft and have the user confirm it is correct. An error in a video is more convincing than the same error in text, so review happens before rendering.

## Step 2: storyboard

A table, one row per shot:

| Shot | Length | Visual | Narration |
|---|---|---|---|
| 1 | 5 s | Title card: "Why gradient descent goes downhill" | This video explains one thing: how gradient descent finds the lowest point. |
| 2 | 10 s | A bowl-shaped surface, a ball resting on its side | Think of the loss function as a bowl. We want the bottom. |
| 3 | 12 s | An arrow at the ball, pointing up the steepest slope | The gradient points up the steepest slope. |
| … | … | … | … |
| last | 6 s | Recap card: three points | To recap… |

Rules:

1. One shot, one idea. Narration follows rung-1 rules (English ≤25 words per sentence; Chinese ≤25 characters).
2. The visual appears before or with the narration, never after it.
3. Open with a title card that says what is coming; close with a recap card.
4. Plan 60–120 seconds. Estimate ~150 English words or ~200 Chinese characters per minute.
5. When a formula appears, color its symbols to match the objects on screen.

## Step 3: toolchain

| Need | Tool | Notes |
|---|---|---|
| Let the coding agent produce the whole video | [showtime](https://github.com/FavioVazquez/showtime) | Open source, renders locally, no API keys. Early by the author's own description. **v0.4.0+ reads this skill's storyboard table directly** (see Step 4). In Claude Code: `/plugin marketplace add FavioVazquez/showtime` |
| Hand-written math animation | [Manim Community](https://www.manim.community/) | Open-source library for 3Blue1Brown-style animation in Python |
| Free local voice | [Kokoro](https://github.com/hexgrad/kokoro) (ONNX: [kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx)) | Local TTS, offline. Listen to the voice for your language first |
| Paid high-quality voice | [ElevenLabs](https://elevenlabs.io/) | Needs an API key |
| Mux video, audio, captions | [ffmpeg](https://ffmpeg.org/) | |

Karpathy's prompt: "Create a 3b1b style video explainer on X", with ElevenLabs for narration. In the replies, people got a free route working with Manim + local Kokoro.

Tools change fast. Open the links and confirm the install steps before recommending them.

## Step 4: deliver

1. The confirmed draft.
2. The storyboard table.
3. **If showtime 0.4.0 or later is installed**, save the storyboard table as `storyboard.md` and hand it over directly:

   ```bash
   showtime new <template> <dir> --from-storyboard storyboard.md
   ```

   It reads the Markdown table with `Shot | Length | Visual | Narration` or `镜头 | 时长 | 画面 | 旁白` headers, in any column order. Check `showtime --help` for the template names.

4. Otherwise, a prompt ready for the video tool, e.g.:

> Create a 3b1b style video explainer on gradient descent, about 90 seconds. Follow this storyboard exactly: [paste storyboard]. Free local TTS voice. Burn in captions.

5. "What to check": which visuals are illustrative rather than real data; formulas and numbers to verify before rendering.

## No video tools?

Fall back to rung 3: turn the storyboard into an HTML page, one card per shot, with a "next" button that plays a CSS/SVG animation and shows the narration as captions. Close to a video, at a fraction of the cost.
