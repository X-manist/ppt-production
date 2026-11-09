# PPT Production

用于制作与修订 PowerPoint 演示文稿的通用 agent skill，包含明确的设计约束、素材要求与验收标准。

## 安装

需要 Node.js 22.20 或更新版本。通过 [skills CLI](https://github.com/vercel-labs/skills) 安装：

```bash
npx skills add yasuo4mushan/ppt-production
```

按提示选择 agent。只安装到 Codex，并在所有项目中使用：

```bash
npx skills add yasuo4mushan/ppt-production --skill ppt-production -a codex -g
```

省略 `-g` 即安装到当前项目。安装方式及其他 agent 参数见 [CLI 文档](https://github.com/vercel-labs/skills/blob/main/docs/commands.md)。

## 使用

在支持显式 skill 调用的 agent 中使用 `$ppt-production`，并提供主题、资料、参考模板和演示要求，例如：

> 使用 $ppt-production，根据我提供的资料制作演示文稿。先给出大纲，澄清关键问题，再搜集素材、并行制作、审核校验并迭代修改。

## 主要规范

- 以用户提供的参考模板为视觉基准。
- 默认统一 Arial，所有可见文字至少 20pt，用户明确指定的例外除外。
- 正文页配备相关主视觉，图片实际嵌入，保持比例，图标可由图片裁切缩小得到。
- 中文文案写成完整句子，标点仅用逗号、句号、问号和冒号。
- 至少三轮交叉验收，检查内容、字体字号、排版、图片和文件完整性。
- 最终 PPTX 必须在真实 PowerPoint 中用副本打开检查。
- 修订前备份，保留用户手改，只修改指定范围。

这是制作与验收规范。实际制稿需要 agent 具备相应的文件处理、素材搜集、子 agent 和 PowerPoint 验证能力。缺少必要验证条件时，应明确报告未通过验收。

## 文件

- [完整 skill](skills/ppt-production/SKILL.md)
- [参考模板使用规范](skills/ppt-production/references/template-guidelines.md)
- [排版与文件工艺](skills/ppt-production/references/pptx-engineering.md)
- [版本记录](CHANGELOG.md)
