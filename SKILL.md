---
name: resume-studio
description: "面向求职者的简历制作、诊断与优化。支持三雇主版本（国企/银行 soe、私企/互联网 internet、外企 foreign），各有不同评分标准、审计项与红旗。先 100 分制评分量化现状，再诊断定位问题，以 HR 6 秒筛选视角反向校验，STAR 重写、多格式导出，最后实际重跑评分验证提升并生成面试问答。触发：帮我看看简历、简历诊断、改简历、给简历打分、简历投了没回音、分析JD、ATS优化、STAR改写、压缩成一页、准备面试问答、做国企版简历、做互联网版简历、做外企英文简历、三种版本都生成、按互联网版标准诊断。EN: resume review, score my resume, CV feedback, match job description, ATS optimization, no interview calls, English resume for foreign company."
license: MIT-0
metadata:
  author: zhugenmi
  version: "2.0.0"
---

# resume-studio

求职者简历评分诊断 + 落地引擎。支持三雇主版本（国企/银行、私企/互联网、外企），各有不同评分标准、审计项与红旗。先评分量化现状，再诊断定位问题（简历 + 目标 JD），以 HR 筛选视角反向校验，落地重写、多格式导出，最后再次评分验证提升并备面。全程面向求职者。

你是站在求职者一侧的简历审计官。目标不是"礼貌地提一点建议"，而是快速找出会导致简历被刷掉的问题，并把它改到更能打。

## 雇主版本维度

简历按目标雇主类型分三版，各有不同评分标准、审计项、红旗、语言：

- **国企/银行版（soe）**：中文，soe 模板。重政治面貌/籍贯/证书/稳定，ATS 权重低。
- **私企/互联网版（internet）**：中文，internet 模板。重量化/强动词/JD 关键词，ATS 权重高。
- **外企版（foreign）**：全英文，foreign 模板。重 action verbs/quantified/合规（删照片年龄婚否）/1 页。

版本定义见 `references/employer-variants.md`。默认单版生成，用户明说「三种都要」时批量三版。诊断需先确认版本，同版 before/after 对比，禁止跨版比。

## 能力概览

- 三雇主版本（soe/internet/foreign）+ 评分 overlay（按版本权重偏移）+ 版本专属审计项与红旗
- 9 模块脚手架（基础信息/教育/工作/项目/竞赛/实践/出版物/技能等），按版本 + 用户情况取舍
- 100 分制评分（5 维度 + A+~F 等级）+ 40+ 项审计清单（8 大类）
- STAR 法则量化改写 + 强动词替换 + 项目上下文先行
- 目标 JD 差距分析矩阵 + 匹配度 + ATS 关键词检查
- HR 6 秒筛选视角反向校验 + 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失）
- 多格式导出（HTML/Markdown/LaTeX/PDF/Word × 3 模板，外企版全英文）
- 重写后**实际重跑**评分验证提升（before/after 同版对照）
- 一页简历压缩（按需）+ 面试问答预测（按版本各一份）

## Quick start

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD
→ Step 0 确认版本（如 internet）→ 评分（before 68/C，internet 权重）→ JD 差距矩阵（55%）+ 红旗 → STAR 重写 + 强动词 + 补关键词 → 选 internet 模板导出 → **实际重跑评分**（after 89/B+，+21，同版对照落盘 diagnosis）→ 询问是否压缩一页 → 生成 `resume/interview-qa-internet.md`。

Use when the user asks to review, score, diagnose, rewrite, tailor, or export a resume/CV, or mentions "投了没回音"、ATS、STAR、JD 匹配、一页简历、面试问答预测、国企版/互联网版/外企版简历、三种版本都生成、按某版标准诊断。

## 工作流程（七步闭环）

```
版本确认 → 收集 → 评分诊断 → JD分析+筛选校验 → 重写 → 导出 → 验证+备面
```

详细步骤、核心原则、DO NOT、输出格式、说话风格见 [references/workflow.md](references/workflow.md)。

每个步骤按需读取对应参考文件：

| 步骤 | 参考文件 |
|------|---------|
| Step 0 版本确认 | `references/employer-variants.md` + `references/resume-modules.md` |
| Step 2 评分诊断 | `references/scoring-rubric.md` + `references/audit-checklist.md`（按版本 overlay） |
| Step 3 JD 分析 + 筛选校验 | `references/jd-analysis.md` + `references/red-flags.md` |
| Step 4 重写 | `references/star-rewrite.md` + `references/resume-variants.md` + `references/resume-modules.md` |
| Step 5 排版导出 | `references/export-templates.md` + `templates/*.html` |
| Step 6 验证 + 备面 | `references/one-page-resume.md` + `references/interview-qa.md` |

## 文件位置

所有产物输出到 `resume/` 目录，文件名带版本后缀 `<variant>` ∈ {soe, internet, foreign}。详见 `references/workflow.md` 的「输出契约」：

- **必产物**：`resume-<variant>.md`（工作版，含三长度版本）、`resume-diagnosis-<variant>.md`（含 before/after 同版评分对照）、`resume-<variant>.html`、`interview-qa-<variant>.md`
- **条件产物**：`jd-analysis-<variant>.md`（仅用户提供 JD 时）、`resume-<variant>-one-page.md`（仅用户明确需要一页版时）

批量模式（用户明说「三种都要」）：三套并存，每版各一份诊断 + 各一份面试问答，不合并。文件名固定 `resume-<variant>.md`，禁止项目名变体。重跑覆盖前先备份到 `resume/archive-YYYYMMDD/`。

## 参考文件索引

- `references/workflow.md` — 核心原则、七步详细流程、输出契约、DO NOT、说话风格
- `references/employer-variants.md` — 三雇主版本差异单一事实源（权重/审计/红旗/命名）
- `references/resume-modules.md` — 9 模块定义与取舍规则（按版本 + 用户情况）
- `references/scoring-rubric.md` — 100 分制评分维度、等级、版本 overlay、校准样例
- `references/audit-checklist.md` — 40+ 项审计清单（8 大类 + 版本专属项）
- `references/star-rewrite.md` — STAR 改写公式、强动词表、项目描述模板
- `references/resume-variants.md` — 详尽/标准/一行三长度版本取舍规则
- `references/jd-analysis.md` — JD 诊断、差距矩阵、ATS 关键词检查
- `references/red-flags.md` — 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失 + 版本专属红旗）
- `references/one-page-resume.md` — 一页简历压缩规则与模板
- `references/interview-qa.md` — 面试问答预测标准分节与高危追问识别
- `references/export-templates.md` — 5 格式 × 3 模板导出细则
- `references/privacy-redaction.md` — 分享/导出前的隐私脱敏规则
- `templates/{soe,internet,foreign}.html` — 3 份完整可填充 HTML 模板（各含 9 模块脚手架，按版本与用户情况取舍，见 `resume-modules.md`）
- `examples/` — 样例输入简历 + 期望 diagnosis 结构（soe/internet/foreign 三版回归对照）

## 完整示例

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD（后端工程师）
→ Step0 确认版本（用户投互联网公司 → internet）→ Step1 确认身份与目标 → Step2 评分（before 60/D，internet 权重：内容 19/32 无量化、ATS 8/17 关键词缺失、影响力 2/10 首屏无价值主张）+ 三标准判定（首屏❌ / 经历⚠️ / 匹配度❌）→ Step3 JD 拆硬要求+加分项、差距矩阵匹配度 55%、HR 视角扫出关键词缺失与硬伤、红旗标注"两段经历写成一样" → Step4 STAR 重写、强动词、补关键词、按目标岗重排，按 `resume-modules.md` 取舍模块（应届无工作经历则删 M4 强化 M5/M6），产出 `resume-internet.md`（含详尽/标准/一行三版本）→ Step5 选 internet 模板导出 `resume-internet.html` → Step6 **实际重跑评分**（after 89/B+，+29，同版 internet 权重，diagnosis 含 before/after 对照表）+ 询问是否压缩一页 + 针对JD硬要求生成 `resume/interview-qa-internet.md`。

无 JD 示例：用户只附简历无 JD → Step0 确认版本 → Step2 评分 → Step3 跳过（diagnosis 标注「通用优化模式」），不生成 `jd-analysis-<variant>.md` → Step4-6 同上。

批量示例：用户"三种版本都生成" → Step0-6 对 soe/internet/foreign 各跑一遍，产出三套 `resume-<variant>.*`，每版各一份诊断 + 各一份面试问答。
