# 多格式导出细则

## 工作格式

以 **Markdown** 为工作格式（版本控制友好、可无损转换），最终再转目标格式。

## HTML 排版规范

- 风格：简约现代，蓝白配色（主蓝 `#2563EB`，浅色背景，非深色）
- 每句话后面加句号
- 「收紧」→ 缩小边距、行间距
- 「放宽」→ 加大边距
- 打印样式必须加 `print-color-adjust: exact` 保持背景色

HTML 基础结构：

```html
<style>
  @media print {
    * { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  }
  body { font-family: -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif; max-width: 800px; margin: 0 auto; padding: 40px; color: #1f2937; }
  h1 { color: #2563EB; }
  h2 { border-bottom: 2px solid #2563EB; padding-bottom: 4px; }
  /* 收紧：margin/padding 减小；放宽：增大 */
</style>
```

## 导出格式（5 种）

| 格式 | 说明 |
|------|------|
| HTML | 自包含、内嵌 CSS、`@media print` 优化 |
| PDF | 浏览器打印另存（Ctrl/Cmd+P → 另存为 PDF） |
| Markdown | 结构清晰、可转其他格式 |
| LaTeX | 完整可编译 `.tex`，XeLaTeX + CJK 中文支持 |
| Word | Pandoc 优化的 Markdown + 转换命令 |

### PDF 导出

优先浏览器手动导出。不用 shell 生成，除非用户已配置 headless 浏览器：

```bash
# 已配置 wkhtmltopdf
wkhtmltopdf resume/resume.html resume/resume.pdf
# 或 weasyprint
weasyprint resume/resume.html resume/resume.pdf
```

### LaTeX 导出

使用 XeLaTeX 引擎支持中文：

```latex
\documentclass[11pt]{article}
\usepackage{fontspec}
\usepackage[UTF8]{ctex}
\setmainfont{Noto Sans CJK SC}
% ... 简历内容
```

### Word 导出

Pandoc 转换：

```bash
pandoc resume/resume.md -o resume/resume.docx --reference-doc=template.docx
```

## 模板风格（4 种）

| 模板 | 风格 | 适用场景 |
|------|------|---------|
| professional | 藏蓝主调、衬线标题、经典边框 | 金融/咨询/法律/医疗 |
| modern | 蓝白点缀、创意布局、图标装饰 | 科技/创业/产品/市场 |
| minimal | 黑白简约、内容密集 | 资深人士/工程师 |
| academic | 正式衬线、多页支持、出版物列表 | 高校教职/科研/博士申请 |

## 中文优化

- 中英文之间自动添加空格
- 中文标点符号规范化
- CJK 字体兼容（LaTeX 用 XeLaTeX 引擎）
- 符合中国大陆求职习惯的排版

## 输出位置

所有导出文件保存到 `resume/` 目录：
- `resume/resume.md`（Markdown 工作版）
- `resume/resume.html`（HTML 版）
- `resume/resume.pdf`（PDF 版）
- `resume/resume.tex`（LaTeX 版）
- `resume/resume.docx`（Word 版）
