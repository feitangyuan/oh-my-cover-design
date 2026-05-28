# Generation Modes

## prompt_mode

Use when the user wants a prompt, wants to paste into another image model, or asks to optimize a cover prompt.

Output:

```text
## 封面提示词

[final prompt]

## 生成建议

- 画幅：竖版 3:4
- 重点：[1-2 things to inspect]

## 本轮记忆

- 保留：[rule]
- 避免：[rule]
```

## image_mode

Use when the user asks to generate the cover image directly.

Workflow:

1. Extract Target.
2. Fill missing critical inputs.
3. If the user provided only article text, ask whether they want to upload reference images before generation.
4. Continue without references only after the user says no references are available or asks to proceed directly.
5. Unless the user explicitly requests one image, generate 3 cover candidates by default.
6. The 3 candidates are not fixed templates. Select them dynamically from the current solution pool according to article goal, available reference images, and material type.
7. If the user provides sample images, prefer solutions induced from those samples. If samples are insufficient, supplement from the built-in 10 composition styles and memory.
8. The 3 candidates must be different layout directions, not minor wording variants.
9. Each candidate must differ from the others on at least two axes: title position, title direction, main visual type, person ratio, information structure, or dominant color.
10. Run Judge Improver on candidate diversity before image generation.
11. Produce one final image prompt per candidate.
12. In Codex, call the image generation capability for each candidate. Current execution is one image per call, so 3 candidates require 3 consecutive calls.
13. Verify each generated image is vertical 3:4.
14. If any image is not 3:4, regenerate with stricter ratio instructions or crop/layout to 1080x1440.
15. Mark progress as `1/3`, `2/3`, and `3/3`; summarize only after all three candidates are complete.
16. Return the 3 candidates with a short label and when to choose each.
17. After the user picks one, refine the selected direction.

Do not create a single collage image containing three candidates unless the user explicitly asks for a comparison sheet. Each candidate should be an independent publishable 3:4 cover.

Solution pool examples:

- 人像大字攻略型
- 清单平铺主视觉型
- 流程/避坑卡片型
- 手写涂鸦纪录片型
- 产品/截图主视觉型
- 对比卡片型
- 极简留白观点型
- 拼贴信息密度型
- 正面对视情绪型
- 局部出镜产品型

These are examples, not a fixed limit. Add or merge solution types when sample induction finds stronger clusters.

Prompt requirements:

- Include platform and aspect ratio: vertical 3:4.
- Default target size: 1080x1440.
- Describe subject, composition, foreground, middle ground, background, lighting, color, typography area, and safe margins.
- If Chinese text must appear, keep it short and clearly quoted, but warn internally that image models may render Chinese incorrectly.

Aspect ratio rules:

- Default output must be vertical 3:4.
- Do not rely only on prompt wording.
- After generation, inspect the actual image dimensions when possible.
- If the ratio is wrong, fix before final delivery: regenerate first, crop/layout second.

## production_mode

Use when the user needs a publishable cover or explicitly cares about readable Chinese text.

Preferred workflow:

1. Generate a no-text or weak-text background image prompt.
2. Reserve clear title space in the prompt.
3. In Codex, generate the background image.
4. Add Chinese title and subtitle using deterministic layout tools when available.
5. Verify text readability, margins, contrast, composition, and vertical 3:4 ratio.

Production prompt rules:

- Do not ask the image model to render long Chinese text.
- Use phrases like "blank title area", "clean empty space for Chinese title", or "large readable typography area".
- Keep the final title outside the generated image when deterministic post-layout is possible.
- Use high contrast between title and background.
- Keep critical text away from face, eyes, product details, and edge margins.

## When Reference Images Exist

- Image 1 is always the face reference.
- Image 2+ are product/UI/material references.
- Do not describe every pixel of a reference image. Use its role: face identity, product screenshot, UI card, logo, object, or texture.
- Do not copy an example cover. Learn composition and hierarchy only.

## People Reference Rules

When a person/child/family reference image exists:

- Treat the reference person as the primary visual source, not as loose inspiration.
- Preserve real-photo texture, age, face shape, hairstyle, clothing color, lighting, and event atmosphere.
- Do not regenerate the person into a generic AI portrait, studio portrait, different age, different face, or unrelated model.
- For parent-child events, sports events, travel records, and real experience posts, prefer using the original reference photo or a crop of it as the base image.
- Add design elements on top: title, stickers, outlines, cards, arrows, labels, and safe-area layout.
- If Codex image generation cannot preserve identity reliably, switch to `production_mode` and create a cover layout over the provided image instead of inventing a new person.
- Only create a new similar person when the user explicitly asks for a fictionalized or replacement character.

## Failure Handling

If Codex image generation is unavailable:

- Complete `prompt_mode`.
- Tell the user the prompt is ready for image generation.
- If `production_mode` was requested, include the no-text background prompt and the exact title layout instruction.

## Codex Notes

- Use Codex image generation for `image_mode`.
- For `production_mode`, prefer generating a clean background without Chinese title text, then add readable Chinese title with deterministic layout when tools are available.
- Do not claim an image was generated unless the image generation call actually succeeds.
