---
name: seedance-cinematic-storyboard
description: Generate Chinese Seedance 2.0, 即梦, or Higgsfield cinematic storyboard prompts with timed shot breakdowns, camera movement, lighting, audio, multi-modal @ references, and long-video continuation plans. Use when the user asks for Seedance, 即梦, AI video, cinematic, movie-quality, film-style, 分镜, 镜头脚本, 视频提示词, storyboard, shot list, product ad, short drama, music video, one-take, video extension, or multi-modal reference prompt writing.
---

# Seedance 电影级分镜提示词

Use this skill to turn a video idea into a paste-ready Seedance 2.0 prompt. Default to Chinese output for 即梦/Seedance unless the user asks for English or Higgsfield-style `@material[name]` syntax.

## Source Note

This skill is an original synthesis of the top open-source Seedance skill patterns found on GitHub. For rankings and upstream links, read `references/top-sources.md` when the user asks about provenance, licenses, or where the method came from.

## Core Workflow

1. Identify the target video: subject, use case, mood, duration, aspect ratio, and target platform.
2. Identify assets: images, videos, audio, first/last frame, character, product, scene, motion, effects, rhythm, dialogue, or music references.
3. Assign each asset an explicit role before writing the prompt.
4. Build a cinematic beat map: 0-2s hook, setup, action, turn/climax, ending frame.
5. Convert the beat map into a timed shot list, then into one paste-ready prompt.
6. Include audio, foley, dialogue, and negative constraints when they affect output quality.
7. For videos longer than 15 seconds, split into segments and use video extension prompts with precise transition frames.

## Platform Constraints To Check

Use these as working constraints unless the user provides newer platform limits:

- Images: up to 9, common formats such as jpg/png/webp, each under about 30 MB.
- Videos: up to 3, usually mp4/mov, each short reference clip about 2-15s.
- Audio: up to 3, usually mp3/wav, total short reference length about 15s.
- Combined files: keep to 12 or fewer.
- Output duration: 4-15 seconds per generation.
- Avoid uploading realistic human face references when the platform may block them.

## Reference Syntax

For 即梦 / Chinese Seedance prompts, prefer:

- `@图片1` for character, first frame, product, environment, or style.
- `@视频1` for camera movement, action, transition, effect, rhythm, or voice reference.
- `@音频1` for BGM, beat, voice tone, or sound effect reference.

For Higgsfield prompts, use `@material[name]` if that is the user’s platform convention.

Always state the role:

```text
@图片1作为主角形象参考，@图片2作为雨夜街道场景参考，参考@视频1的手持跟拍运镜和节奏，背景音乐参考@音频1。
```

## Cinematic Prompt Formula

A strong Seedance storyboard prompt should contain:

```text
[时长/比例/风格总纲] + [0-2秒视觉钩子] + [时间戳分镜] + [主体动作] + [镜头语言] + [光影色调] + [声音/对白/音效] + [素材引用说明] + [禁止项]
```

Use time stamps for anything 9 seconds or longer. For 4-8 seconds, keep the prompt focused on one clear action and one main camera idea.

## Shot List Before Final Prompt

When the user asks for “分镜”, “storyboard”, or a cinematic plan, output a compact shot table first, then the final prompt.

Recommended table columns:

```text
时间 | 景别 | 画面/动作 | 运镜 | 光影/色调 | 声音
```

Keep the table short enough to be useful, then provide the final prompt under `可复制提示词`.

## 0-2s Hook Patterns

Use one strong opening hook, or stack two if the user wants social-platform impact:

- Extreme close-up to wide reveal: start with a tiny detail, then reveal the full scene.
- Black screen to light burst: silence or darkness, then sudden image and sound.
- Reverse motion: smoke, water, glass, fabric, or debris moving unnaturally backward.
- Fast object entering frame: motion from an edge of the frame, not the center.
- Rack focus reveal: blurred foreground/background switching focus at the beat.
- Eye contact: a character’s eyes open or lock onto camera.
- Scale shock: tiny human in vast architecture/nature, or huge object in a cramped place.

## Camera Vocabulary

Use precise cinematic language instead of vague “make it cool” wording:

- 景别: 大远景、远景、全景、中景、近景、特写、大特写。
- 运镜: 缓慢推镜、拉远揭示、侧向跟拍、手持跟拍、环绕、俯拍、仰拍、摇移、航拍、升降镜头、一镜到底。
- 专业效果: 希区柯克变焦、焦点转移、浅景深、遮挡转场、甩镜转场、硬切、慢动作、升格、鱼眼镜头、第一人称 POV。
- 构图: 三分法、对称构图、负空间、框中框、前中后景层次、引导线。

## Lighting And Color

Specify light direction, mood, and color contrast:

- 黄金时刻暖光: nostalgia, romance, healing, epic reveal.
- 霓虹冷暖对比: cyberpunk, fashion, nightlife, tech.
- 高反差黑色电影: suspense, crime, betrayal, power.
- 体积光和雾: fantasy, sacred, mystery, dream.
- 柔和室内实用灯: intimacy, farewell, quiet drama.
- 冷蓝月光: solitude, danger, melancholy.

## Audio Layer

Always add sound when it helps the result:

- BGM mood: grand, tense, sparse piano, electronic pulse, orchestral swell.
- Foley: footsteps, cloth movement, metal scrape, paper tear, water drop, product click.
- Dialogue: put lines in quotes and label role plus emotion.
- Beat sync: mark exact visual moments that should hit the music beat.

Example:

```text
声音：0-2秒几乎静音，只保留雨滴声；2秒鼓点落下时画面硬切到全景；随后低频电子乐进入，脚步声和衣料摩擦与镜头推进同步。
```

## Output Formats

### Simple Single Prompt

Use when the user already knows what they want:

```text
## 可复制提示词

[完整中文提示词]

## 素材说明

- @图片1: [用途]
- @视频1: [用途]
- @音频1: [用途]
```

### Cinematic Storyboard Prompt

Use when the user asks for film-level shot planning:

```text
## 分镜表

| 时间 | 景别 | 画面/动作 | 运镜 | 光影/色调 | 声音 |
|---|---|---|---|---|---|
| 0-2秒 | 特写 | ... | ... | ... | ... |

## 可复制提示词

[把分镜表压缩成一段可直接粘贴到 Seedance 的自然中文提示词]

## 检查项

- 时长: [x秒]
- 比例: [16:9 / 9:16 / 1:1]
- 引用素材: [清单]
- 禁止项: [字幕、水印、无关文字、风格漂移等]
```

### Long Video Plan

Use for more than 15 seconds:

```text
## 超长视频方案

主题: [一句话]
总时长: [x秒]
总段数: [n段]
比例: [建议]

### 第1段 0-15秒: 正常生成

生成时长: 15秒
可复制提示词: [完整提示词]
衔接点: [结尾画面必须精确描述]

### 第2段 15-30秒: 视频延长

操作: 将第1段成片上传为@视频1
生成时长: 15秒
可复制提示词: 将@视频1延长15秒。[承接上段结尾继续写]
衔接点: [结尾画面]
```

## Quality Rules

- Prefer concrete nouns and visible actions over abstract adjectives.
- Do not overload 4-6 seconds with multiple locations and plot turns.
- Give every uploaded asset a purpose; never write a bare `参考@视频1`.
- Avoid conflicting instructions such as “固定镜头” and “环绕镜头” in the same moment.
- Keep character/product identity anchored to the same reference image across shots.
- Match image-reference style to the target video style.
- Put dialogue, sound, and camera timing in the same timeline when synchronization matters.
- Add concise negative constraints: no watermark, no random text, no subtitles unless requested, no extra logos, no style drift.

## Default Questions

Ask only what is needed. If the user gives enough context, proceed directly.

- 时长和比例是什么？如果未说明，推荐 15秒、16:9；短视频平台推荐 9:16。
- 是否有参考图片、视频或音乐？如果有，给每个素材编号和用途。
- 目标风格更偏电影、广告、短剧、MV、产品展示、还是一镜到底？

## Default Delivery Style

Output in concise Chinese. Lead with the final usable prompt unless the user explicitly asks for analysis. When giving multiple versions, keep it to 2 strong options: one safer, one more cinematic/ambitious.
