# Oh My Cover Design

把文章扔给 agent，它读完内容、问你几个问题，然后输出一段可以直接跑图的封面提示词。标题自动帮你想，构图逻辑全内置好了。

支持 Claude Code、Codex，以及任何支持自定义 skill 的 AI agent。

---

## 效果

<table>
  <tr>
    <td><img src="assets/examples/01-双面特工.png" width="180"/></td>
    <td><img src="assets/examples/02-再见了Figma.png" width="180"/></td>
    <td><img src="assets/examples/03-角色一致.png" width="180"/></td>
    <td><img src="assets/examples/04-动画自由.png" width="180"/></td>
  </tr>
  <tr>
    <td><img src="assets/examples/05-Claude鞭子.png" width="180"/></td>
    <td><img src="assets/examples/06-MYTHOS.png" width="180"/></td>
    <td><img src="assets/examples/07-前端设计.png" width="180"/></td>
    <td><img src="assets/examples/08-养虾必备.png" width="180"/></td>
  </tr>
</table>

---

## 怎么用

把文章内容发给 agent，skill 自动触发，然后一个问题一个问题地问你：

选哪种构图风格、有没有人脸参考图、人物表情、有没有产品截图要放进去、背景色调、字体……

问完，输出提示词，拿去跑图。不需要懂设计，不需要自己写提示词。

---

## 10 种构图风格

| 风格 | 适合什么 |
|------|---------|
| 深色渐变风 | 人物居中，大字压在后面，冲击力最强 |
| 纯色扁平风 | 干净清爽，人物 + 道具 + 纯色背景 |
| 产品主视觉风 | 有 UI 截图或产品图时首选，截图占主体 |
| 对比卡片风 | 前后对比、好坏对比类内容专用 |
| 极简留白风 | 大留白，标题是唯一焦点，克制感强 |
| 海报拼贴风 | 素材多的时候用，多层叠加，纵深感强 |
| 人物侧置留白风 | 人物偏一侧，另一边全给标题，大气 |
| 背影构图风 | 人物背对镜头，适合励志、启发类内容 |
| 局部出镜风 | 只露手或半张脸，产品是绝对主角 |
| 正面对视风 | 直视镜头，眼神接触，情绪直接 |

---

## 安装

```bash
git clone https://github.com/feitangyuan/oh-my-cover-design.git \
  ~/.claude/skills/cover-design-open
```

只想要 SKILL.md：

```bash
mkdir -p ~/.claude/skills/cover-design-open
curl -o ~/.claude/skills/cover-design-open/SKILL.md \
  https://raw.githubusercontent.com/feitangyuan/oh-my-cover-design/main/SKILL.md
```

---

## 关于参考图

- **图1**：你自己的人脸照，skill 会在提示词里保持五官一致性
- **图2 起**：想放进封面的任何素材——产品图、UI 截图、品牌资产都行

---

## License

MIT
