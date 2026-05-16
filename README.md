# Oh My Cover Design

封面这个事儿一直很折磨我。

我大概知道什么样的封面吸引人，但自己就是搞不出来。不管怎么学都学不会设计工具。

后来 AI 图片生成开始能用了，我开始尝试用它做封面。虽然早期人脸经常变形，但整体效果已经比我自己搞的好太多了。从那时候开始，我所有的封面，都是用 AI agent + 图片生成出的。

问题是——提示词很难写。写不好就出废图。

所以我花了很长时间，把自己摸索出来的一套封面提示词逻辑，全部打包进了这个 skill。现在把它开源了。

---

## 效果

这些封面都是用这套 skill 生成的提示词跑出来的：

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

## 它帮你做什么

装好之后，你只需要把文章内容发给 agent。

skill 读完文章，会开始一个问题一个问题地问你：

- 想用哪种构图风格（10 种选一）
- 有没有人脸参考图
- 人物表情选哪种
- 有没有产品图、UI截图等额外素材
- 背景色调
- 字体风格和颜色

问完之后，输出一段精准的提示词。拿去跑图就行了。

封面标题也会根据文章内容自动帮你想，不满意直接改。

---

## 10 种构图风格

不是那种花里胡哨、密密麻麻的图。都是带视觉创意、又保持简洁清晰的类型。

| 风格 | 特点 |
|------|------|
| 深色渐变风 | 人物居中，大字覆盖后方，高对比强冲击 |
| 纯色扁平风 | 人物抠图感，纯色背景，干净清爽 |
| 产品主视觉风 | UI截图/产品占主体，人物做引导手势 |
| 对比卡片风 | 人物手持两张对比卡片，适合前后对比内容 |
| 极简留白风 | 大面积留白，文字是主视觉锤 |
| 海报拼贴风 | 多张参考图叠加，分层有纵深 |
| 人物侧置留白风 | 人物偏一侧，大面积留给标题，版面大气 |
| 背影构图风 | 人物背对镜头，制造代入感和想象空间 |
| 局部出镜风 | 只露手/半脸/侧脸，产品是绝对主角 |
| 正面对视风 | 直视镜头，眼神接触，文字环绕脸部 |

---

## 安装

支持 Claude Code、Codex，以及任何支持 skill / 自定义指令的 AI agent。

**Claude Code / Codex：**

```bash
git clone https://github.com/feitangyuan/oh-my-cover-design.git \
  ~/.claude/skills/cover-design-open
```

或者只下载 SKILL.md：

```bash
mkdir -p ~/.claude/skills/cover-design-open
curl -o ~/.claude/skills/cover-design-open/SKILL.md \
  https://raw.githubusercontent.com/feitangyuan/oh-my-cover-design/main/SKILL.md
```

装好之后，把文章扔给 agent，skill 会自动触发。

---

## 关于参考图

- **图1**：你自己的人脸照片，skill 会保持五官一致性
- **图2 起**：UI截图、产品图、任何你想放进封面的素材

提示词里会自动用「参考图1/图2/图3」这样的方式引用，直接投喂图片生成模型就行。

---

## License

MIT
