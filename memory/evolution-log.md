# Evolution Log

Use this file only when persistent evolution is requested.

Append lightweight observations. Do not promote single-run observations directly into `SKILL.md`.

```yaml
# Example
date: YYYY-MM-DD
task_type: "cover_generation"
article_type: ""
mode: "prompt_mode"
style_used: ""
title_used: ""
judge_weakness: ""
improvement_action: ""
final_direction: ""
keep:
  - ""
avoid:
  - ""
feedback_source: "self"
confidence: "low"
```

```yaml
date: 2026-05-26
task_type: "cover_generation"
article_type: "亲子赛事/活动攻略"
mode: "image_mode"
style_used: "大字人像攻略封面"
title_used: "雨后斯巴达避坑"
judge_weakness: "用户只提供正文时直接生成图片，未先询问人脸、现场素材或风格参考图。"
improvement_action: "在 image_mode / production_mode 中加入参考图确认步骤；用户明确无参考图后才生成无参考图版本。"
final_direction: "先问参考图，再生成。"
keep:
  - "只给正文且请求出图时，先询问参考图能提高人物一致性、现场真实感和风格对齐。"
avoid:
  - "不要在用户未确认参考图需求时直接调用图片生成。"
feedback_source: "human"
confidence: "high"
```

```yaml
date: 2026-05-26
task_type: "cover_generation"
article_type: "小红书封面通用"
mode: "image_mode"
style_used: "any"
title_used: ""
judge_weakness: "只在提示词中写竖版 3:4，不足以保证图片工具实际输出符合小红书封面比例。"
improvement_action: "加入默认 1080x1440 和生成后 3:4 画幅校验；比例错误时优先重生成，其次裁切/排版成 1080x1440。"
final_direction: "默认 3:4 必须成为生成后校验规则。"
keep:
  - "小红书封面默认竖版 3:4，目标尺寸 1080x1440。"
  - "出图后要检查实际画幅，不符合就修正后再交付。"
avoid:
  - "不要只靠提示词声明 3:4 就直接交付。"
feedback_source: "human"
confidence: "high"
```

```yaml
date: 2026-05-26
task_type: "cover_generation"
article_type: "亲子攻略/清单/避坑"
mode: "image_mode"
style_used: "大字人像攻略封面"
title_used: "杭州斯巴达必看"
judge_weakness: "连续生成时复用了相同的顶部大标题、中部贴纸、底部副标题结构，导致新图和上一张差异不足。"
improvement_action: "将 image_mode 默认升级为一次生成 3 张候选图；候选之间必须改变至少两个维度，并先检查版式差异。"
final_direction: "先给用户 3 个明显不同的封面方向，再基于赢家精修。"
keep:
  - "默认三候选：人像大字攻略型、清单平铺主视觉型、流程/避坑卡片型。"
  - "候选图必须先保证版式差异，再优化单张质量。"
avoid:
  - "不要连续复用同一个标题布局，只换文案和素材。"
feedback_source: "human"
confidence: "high"
```

```yaml
date: 2026-05-27
task_type: "cover_generation"
article_type: "小红书封面通用"
mode: "image_mode"
style_used: "dynamic_solution_pool"
title_used: ""
judge_weakness: "默认三候选被写成固定的人像攻略、清单平铺、流程避坑三种，容易限制样图归纳和内容适配。"
improvement_action: "将默认三候选改为从当前解决方案池动态选择 3 个方向；样图归纳出的方案优先，内置风格和 memory 作为补充。"
final_direction: "一次出 3 张，但不是固定三种；候选来自可进化的解决方案池。"
keep:
  - "三候选是数量策略，不是固定模板集合。"
  - "候选方向应根据正文、素材、样图聚类和记忆动态选择。"
avoid:
  - "不要把默认三候选固化为仅有三种解决方案。"
feedback_source: "human"
confidence: "high"
```

```yaml
date: 2026-05-27
task_type: "cover_generation"
article_type: "亲子赛事/真人经历"
mode: "image_mode"
style_used: "dynamic_solution_pool"
title_used: ""
judge_weakness: "人物生成质感不够真实，且没有严格按照用户提供的人物参考图生成。"
improvement_action: "加入人物参考图优先级：真实人物、年龄感、发型、服装、现场光线和纪实质感必须优先保留；无法稳定保持一致时切换 production_mode，用原图或裁切图做底图再排版。"
final_direction: "真人经历类封面优先保留原图人物，不凭空重画 AI 感人物。"
keep:
  - "人物/亲子参考图是主视觉源，不是松散灵感。"
  - "亲子赛事、活动现场、真实经历类封面优先原图底图 + 后期排版。"
avoid:
  - "不要把参考人物重画成通用 AI 人像或不相干人物。"
feedback_source: "human"
confidence: "high"
```

```yaml
date: 2026-05-27
task_type: "cover_generation"
article_type: "小红书封面通用"
mode: "image_mode"
style_used: "three_candidate_execution"
title_used: ""
judge_weakness: "用户期望三候选，但当前图片工具一次调用只生成一张；中途打断会导致只生成 1-2 张。"
improvement_action: "明确三候选需要连续调用 3 次，按 1/3、2/3、3/3 标记进度，三张完成后再总结；不要做三宫格替代独立封面。"
final_direction: "三候选 = 三张独立 3:4 封面，连续生成。"
keep:
  - "三候选模式下每张都是可发布的独立 3:4 封面。"
  - "生成进度应标记为 1/3、2/3、3/3。"
avoid:
  - "不要默认把三张候选拼成一张对比图。"
feedback_source: "human"
confidence: "high"
```
