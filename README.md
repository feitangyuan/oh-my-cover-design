# Oh My Cover Design

用 Claude Code + AI 图片生成，做出高质量的公众号 / 小红书封面。

把文章扔给 Claude，它会问你几个问题，然后输出一段可以直接跑图的提示词。

---

## 效果展示

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

## 使用流程

1. 把文章内容发给 Claude，说「帮我设计封面」
2. Claude 逐步问你 8 个问题（风格、人物、表情、素材、配色、字体…）
3. 拿到提示词，去图片生成模型跑图

---

## 10 种构图风格

| # | 风格 | 适合场景 |
|---|------|---------|
| 1 | **深色渐变风** | 人物居中，大字覆盖后方，高对比强冲击 |
| 2 | **纯色扁平风** | 人物抠图感，纯色背景，干净清爽 |
| 3 | **产品主视觉风** | UI截图/产品占主体，有素材图时首选 |
| 4 | **对比卡片风** | 人物手持两张对比卡片，适合前后对比内容 |
| 5 | **极简留白风** | 大面积留白，文字是主视觉锤 |
| 6 | **海报拼贴风** | 多张参考图叠加，分层有纵深 |
| 7 | **人物侧置留白风** | 人物偏一侧，大面积留给标题，版面大气 |
| 8 | **背影构图风** | 人物背对镜头，制造代入感和想象空间 |
| 9 | **局部出镜风** | 只露手/半脸/侧脸，产品是绝对主角 |
| 10 | **正面对视风** | 直视镜头，眼神接触，文字环绕脸部 |

---

## 安装

需要已安装 [Claude Code](https://claude.ai/code)。

```bash
mkdir -p ~/.claude/skills/cover-design-open
curl -o ~/.claude/skills/cover-design-open/SKILL.md \
  https://raw.githubusercontent.com/feitangyuan/oh-my-cover-design/main/SKILL.md
```

或者直接 clone：

```bash
git clone https://github.com/feitangyuan/oh-my-cover-design.git \
  ~/.claude/skills/cover-design-open
```

---

## 多参考图支持

- **图1**：人脸参考图，保持五官一致性
- **图2 起**：UI截图、产品图、其他素材，skill 会把它们融入构图

---

## License

MIT
