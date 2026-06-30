# 多格式导出细则

## 工作格式

以 **Markdown** 为工作格式（版本控制友好、可无损转换），最终再转目标格式。Markdown 工作版含三长度版本（详尽/标准/一行），见 `resume-variants.md`。

## 模板选择（3 种 HTML 模板）

三份**完整可填充**的 HTML 模板位于 `templates/` 目录，直接选用并填充内容，不要即兴自创样式：

| 模板文件 | 风格 | 适用场景 |
|---------|------|---------|
| `templates/soe.html` | 藏蓝主调、衬线标题、经典边框 | 央企/国企/银行/事业单位 |
| `templates/internet.html` | 蓝白卡片、图标装饰、关键词 tag | 民营科技/互联网/创业 |
| `templates/foreign.html` | 黑白简约、内容密集、无装饰 | 跨国/外资/海外岗 |

选择规则：用户指定 → 用指定的；否则按**目标雇主版本**默认映射（见 `employer-variants.md`）：

| 版本 | 默认模板 | 语言 |
|------|---------|------|
| soe（国企/银行） | soe.html | 中文 |
| internet（私企/互联网） | internet.html | 中文 |
| foreign（外企） | foreign.html | 全英文 |

文件名带版本后缀 `resume-<variant>.html`。

模板内含 9 模块脚手架，按版本与用户情况取舍模块，见 `resume-modules.md`。

## HTML 排版规范（所有模板共用）

- **简洁硬约束**：所有模板统一简洁风格，≤2 色、无装饰图标（▸/■ 等）、无彩色背景块、无彩色边框装饰。重点靠字号层级 + 留白 + 强动词，不靠花哨配色。主色：internet/soe 用单色强调（`#111827` 或藏蓝 `#1e3a8a`），foreign 黑白。
- 浅色背景，**非深色**（用户偏好浅色专业风）
- 所有模板已内嵌 `print-color-adjust: exact`
- 「收紧」→ 缩小 padding/line-height；「放宽」→ 加大 padding
- 中英文之间加空格；每句话后加句号（中文简历）
- 填充时替换所有 `{{占位符}}`，删除模板里的 `<!-- 填充：... -->` 注释

## 导出格式（5 种）

| 格式 | 说明 |
|------|------|
| HTML | 自包含、内嵌 CSS、`@media print` 优化（从 3 模板选一） |
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
- `resume/resume.html`（HTML 版，从 3 模板选一）
- `resume/resume.pdf`（PDF 版，浏览器另存）
- `resume/resume.tex`（LaTeX 版，按需）
- `resume/resume.docx`（Word 版，按需）
