# Input Schema

Use this schema when the user provides structured parameters or asks for direct generation.

## Fields

```yaml
article: ""              # Required unless title and visual_brief are both provided
platform: "xiaohongshu"  # fixed target platform
mode: "auto"             # auto | prompt_mode | image_mode | production_mode
style: "auto"            # auto or one of the 10 built-in cover styles
title: ""                # Optional. If empty, generate 1-3 candidates
subtitle: ""             # Optional
audience: ""             # Optional. Who should click
emotion: "auto"          # auto | 震惊 | 好奇 | 专业 | 温暖 | 反差 | 危机感 | 获得感
color_tone: "auto"       # auto | 浅色系 | 深色系 | 暖色调 | 冷色调 | 高饱和撞色
font_style: "auto"       # auto | 超粗黑体 | 柔和圆体 | 手写涂鸦体 | 极简无衬线 | 复古宋体
font_color: "auto"       # auto | 纯白 | 纯黑 | 渐变色 | 描边效果
person:
  face_ref: null         # Optional. Image 1, fixed as face reference
  description: ""        # Used when no face_ref is provided
  expression: "auto"
assets: []               # Optional. Image 2+, UI screenshots, product images, brand assets
visual_brief: ""         # Optional. User-specified visual idea
constraints: []          # Optional. Brand, legal, text, ratio, forbidden elements
```

## Defaults

- `platform: xiaohongshu`: use vertical 3:4 cover unless the user asks otherwise.
- `style: auto`: choose the style by article goal and available assets.
- `mode: auto`: infer from user wording.
- `title: ""`: generate 1-3 short candidates, 4-8 Chinese characters by default.
- `emotion: auto`: infer from article value proposition and audience pain.

## Missing Information

Ask only one question at a time.

Ask only for information that affects the next decision:

- If the user only provides article text and requests `image_mode` or `production_mode`, ask whether they want to upload reference images before generating.
- Ask for three optional reference types: face/person reference, scene/product material, and style sample.
- If the user says there are no reference images or asks to proceed directly, generate a no-reference version.
- If `image_mode` or `production_mode` needs a human face and no face is provided, ask whether to use a reference face or a described person.
- If a face/person reference is provided for a real event or real person post, keep that person as the primary visual source; do not replace them with a generated lookalike unless the user explicitly asks.
- If the chosen style requires product/UI material and no asset is provided, ask for the asset or recommend a different style.
- If title is missing, generate candidates instead of asking immediately.
- If color/font are missing, infer them from style and article emotion.

## Direct Invocation Example

```yaml
article: "这篇文章讲如何用 AI Agent 自动生成小红书封面..."
platform: "xiaohongshu"
mode: "image_mode"
style: "auto"
person:
  description: "年轻女性，干练，科技博主气质"
assets:
  - "一张产品界面截图"
emotion: "好奇"
```
