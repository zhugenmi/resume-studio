# 多格式导出细则

## 工作格式

以 **Markdown** 为工作格式（版本控制友好、可无损转换），最终再转目标格式。Markdown 工作版含三长度版本（详尽/标准/一行），见 `resume-variants.md`。

## 模板选择（4 种 HTML 模板）

四份**完整可填充**的 HTML 模板位于 `templates/` 目录，直接选用并填充内容，不要即兴自创样式：

| 模板文件 | 风格 | 适用场景 |
|---------|------|---------|
| `templates/professional.html` | 藏蓝主调、衬线标题、经典边框 | 金融/咨询/法律/医疗 |
| `templates/modern.html` | 蓝白卡片、图标装饰、关键词 tag | 科技/创业/产品/市场 |
| `templates/minimal.html` | 黑白简约、内容密集、无装饰 | 资深人士/工程师 |
| `templates/academic.html` | 正式衬线、多页支持、含出版物列表 | 高校教职/科研/博士申请 |

选择规则：用户指定 → 用指定的；否则按目标岗位领域默认选（金融法律→professional，科技产品→modern，资深工程师→minimal，学术→academic）。

## HTML 排版规范（所有模板共用）

- 主蓝 `#2563EB`（professional/academic 用藏蓝 `#1e3a8a` 主调）
- 浅色背景，**非深色**（用户偏好浅色专业风）
- 所有模板已内嵌 `print-color-adjust: exact`
- 「收紧」→ 缩小 padding/line-height；「放宽」→ 加大 padding
- 中英文之间加空格；每句话后加句号（中文简历）
- 填充时替换所有 `{{占位符}}`，删除模板里的 `<!-- 填充：... -->` 注释

## 导出格式（5 种）

| 格式 | 说明 |
|------|------|
| HTML | 自包含、内嵌 CSS、`@media print` 优化（从 4 模板选一） |
| PDF | 浏览器打印另存（Ctrl/Cmd+P → 另存为 PDF），边距设「无」或「最小」 |
| Markdown | 结构清晰、可转其他格式（工作版，含三长度版本） |
| LaTeX | 完整可编译 `.tex`，XeLaTeX + CJK 中文支持 |
| Word | Pandoc 从 Markdown 转换 |

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

## 中文优化

- 中英文之间自动添加空格
- 中文标点符号规范化
- CJK 字体兼容（LaTeX 用 XeLaTeX 引擎）
- 符合中国大陆求职习惯的排版

## 输出位置

所有导出文件保存到 `resume/` 目录：
- `resume/resume.md`（Markdown 工作版，含三长度版本）
- `resume/resume.html`（HTML 版，从 4 模板选一）
- `resume/resume.pdf`（PDF 版，浏览器另存）
- `resume/resume.tex`（LaTeX 版，按需）
- `resume/resume.docx`（Word 版，按需）
