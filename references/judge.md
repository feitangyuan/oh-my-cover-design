# Cover Judge Improver

Use this judge before final output or image generation.

The judge does not score. The judge must turn evaluation into improvement.

## Loop

Run this internally:

```text
Draft
→ Critique
→ Mutation Plan
→ Revised Draft
→ Final Check
```

Do not expose the whole loop unless the user asks for reasoning.

## Critique

Find the most important weakness first. Prefer one decisive issue over many minor comments.

For `image_mode`, first judge candidate diversity before judging individual quality.

Candidate diversity must be real:

- Do not reuse the same title block layout across all candidates.
- Do not keep the same top-title / middle-sticker / bottom-subtitle structure unless the user requested that exact structure.
- At least two axes must change between candidates: title position, title direction, main visual type, person ratio, information structure, dominant color, or first attention point.
- If candidates feel like the same cover with different words, revise before image generation.

Candidate set selection:

- Do not force a fixed A/B/C set.
- Select 3 directions from the current solution pool based on article goal, available reference images, and strongest visual evidence.
- If the user has provided recent sample clusters, prefer those sample-derived solution types.
- If the selected 3 directions are all from the same family, replace at least one with a structurally different direction.
- The final 3 should feel like real alternatives, not variations of the same cover.

Check:

- **一眼读懂**：3 seconds以内是否能看懂主题。
- **点击冲击**：标题、情绪、视觉反差是否足够让目标受众停下。
- **主视觉清晰**：人物、标题、产品、道具谁是第一主角是否明确。
- **人物真实感**：有人物参考图时，是否保留真实人物和现场质感，而不是生成 AI 感新人像。
- **风格匹配**：构图风格是否适合文章内容、素材数量和平台。
- **图片可生成性**：提示词是否具体、稳定，是否避免复杂矛盾指令。
- **文字可读性**：标题是否短，位置、颜色、遮挡关系是否合理。
- **安全区**：关键元素是否远离边缘，适合小红书封面裁切。
- **差异化**：是否避免通用模板感、廉价科技感、过度堆元素。

## Red Flags

If any red flag appears, create a mutation plan:

- Title is longer than 8 Chinese characters without strong reason.
- Main visual is abstract: "AI", "效率", "成长", "系统" without a concrete object.
- Face, product, and title compete for first attention.
- The prompt asks for holograms, data streams, particles, or excessive glow effects.
- The text is placed over a busy area.
- Product screenshots are too small to read.
- The style requires assets that are not available.
- Emotion, expression, color, and title point in different directions.
- The prompt over-describes the reference image instead of assigning its role.
- The image model is asked to render long Chinese text.
- A real person reference exists, but the draft replaces them with a generic AI portrait or unrelated person.
- A real event photo exists, but the draft ignores its documentary value and invents a fake studio-like scene.

## Mutation Plan

A mutation plan must be concrete enough to rewrite the draft immediately.

Use this format internally:

```text
Weakness: [the main problem]
Why it hurts: [impact on Xiaohongshu cover quality]
Change: [specific edit]
Revised direction: [new title / composition / visual / prompt instruction]
```

Mutation options:

- **Title**：shorten, make more concrete, add identity, result, conflict, or curiosity.
- **Composition**：move from centered to side layout, from collage to product focus, or from product focus to title focus.
- **Main Visual**：replace abstract idea with object, card, interface, gesture, comparison, or scene.
- **Emotion**：align expression, title, color, and action around one feeling.
- **Readability**：reserve blank area, increase contrast, reduce elements, simplify title.
- **Generation Stability**：remove conflicting instructions, reduce object count, clarify foreground/middle/background.
- **Production Safety**：switch to no-text background plus deterministic Chinese title layout.

## Revised Draft

Apply the mutation plan directly.

The revised draft should be visibly better in at least one of these ways:

- Easier to understand at a glance.
- More concrete and imageable.
- Clearer hierarchy between title, person, and product.
- More stable for image generation.
- Safer for readable Chinese typography.
- More like a Xiaohongshu cover, less like a generic poster.

## Final Check

Stop if:

- No clear improvement action remains.
- The next change would only swap words without improving composition.
- Further changes would make the cover busier.
- Readability or image stability starts getting worse.
- User asks for quick output.

Continue for one more revision if:

- The title is still vague.
- The main visual is still abstract.
- The first attention point is still unclear.
- Chinese text is still delegated to the image model in a risky way.
- The prompt still contains conflicting or overloaded instructions.

Default maximum: 2 improvement rounds.

## Memory Format

Keep memory short:

```text
- 保留：[specific reusable rule]
- 避免：[specific failure pattern]
```

Good memory examples:

- 保留：AI工具类文章用“产品主视觉 + 人物指向 + 4字结果标题”更稳。
- 避免：让模型直接生成长中文标题，容易错字和变形。
- 保留：对比类内容优先用一亮一暗两张卡片，读者能一眼理解 before/after。
