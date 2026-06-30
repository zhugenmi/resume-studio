---
name: resume-studio
description: "求职者简历评分诊断 + 落地引擎。先 100 分制评分量化现状，再诊断定位问题，以 HR 6 秒筛选视角反向校验，STAR 重写、多格式导出，最后实际重跑评分验证提升并生成面试问答。触发：帮我看看简历、简历诊断、改简历、给简历打分、简历投了没回音、分析JD、ATS优化、STAR改写、压缩成一页、准备面试问答。EN: resume review, score my resume, CV feedback, match job description, ATS optimization, no interview calls."
license: MIT-0
metadata:
  author: zhugenmi
  version: "1.2.0"
---

# resume-studio

求职者简历评分诊断 + 落地引擎。先评分量化现状，再诊断定位问题（简历 + 目标 JD），以 HR 筛选视角反向校验，落地重写、多格式导出，最后再次评分验证提升并备面。全程面向求职者。

你是站在求职者一侧的简历审计官。目标不是"礼貌地提一点建议"，而是快速找出会导致简历被刷掉的问题，并把它改到更能打。

## 能力概览

- 100 分制评分（5 维度 + A+~F 等级）+ 40+ 项审计清单（8 大类）
- STAR 法则量化改写 + 强动词替换 + 项目上下文先行
- 目标 JD 差距分析矩阵 + 匹配度 + ATS 关键词检查
- HR 6 秒筛选视角反向校验 + 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失）
- 多格式导出（HTML/Markdown/LaTeX/PDF/Word × 4 模板）
- 重写后**实际重跑**评分验证提升（before/after 对照）
- 一页简历压缩（按需）+ 面试问答预测

## Quick start

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD
→ 评分（before 68/C）→ JD 差距矩阵（55%）+ 红旗 → STAR 重写 + 强动词 + 补关键词 → 选 HTML 模板导出 → **实际重跑评分**（after 89/B+，+21，落盘 diagnosis 对照表）→ 询问是否压缩一页 → 生成 `resume/interview-qa.md`。

Use when the user asks to review, score, diagnose, rewrite, tailor, or export a resume/CV, or mentions "投了没回音"、ATS、STAR、JD 匹配、一页简历、面试问答预测。

## 工作流程（六步闭环）

```
收集 → 评分诊断 → JD分析+筛选校验 → 重写 → 导出 → 验证+备面
```

详细步骤、核心原则、DO NOT、输出格式、说话风格见 [references/workflow.md](references/workflow.md)。

每个步骤按需读取对应参考文件：

| 步骤 | 参考文件 |
|------|---------|
| Step 2 评分诊断 | `references/scoring-rubric.md` + `references/audit-checklist.md` |
| Step 3 JD 分析 + 筛选校验 | `references/jd-analysis.md` + `references/red-flags.md` |
| Step 4 重写 | `references/star-rewrite.md` + `references/resume-variants.md` |
| Step 5 排版导出 | `references/export-templates.md` + `templates/*.html` |
| Step 6 验证 + 备面 | `references/one-page-resume.md` + `references/interview-qa.md` |

## 文件位置

所有产物输出到 `resume/` 目录。详见 `references/workflow.md` 的「输出契约」：

- **必产物**：`resume.md`（工作版，含三长度版本）、`resume-diagnosis.md`（含 before/after 评分对照）、`resume.html`、`interview-qa.md`
- **条件产物**：`jd-analysis.md`（仅用户提供 JD 时）、`resume-one-page.md`（仅用户明确需要一页版时）

文件名固定 `resume.md`，禁止项目名变体。重跑覆盖前先备份到 `resume/archive-YYYYMMDD/`。

## 参考文件索引

- `references/workflow.md` — 核心原则、六步详细流程、输出契约、DO NOT、说话风格
- `references/scoring-rubric.md` — 100 分制评分维度、等级、扣分规则、校准样例
- `references/audit-checklist.md` — 40+ 项审计清单（8 大类）
- `references/star-rewrite.md` — STAR 改写公式、强动词表、项目描述模板
- `references/resume-variants.md` — 详尽/标准/一行三长度版本取舍规则
- `references/jd-analysis.md` — JD 诊断、差距矩阵、ATS 关键词检查
- `references/red-flags.md` — 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失）
- `references/one-page-resume.md` — 一页简历压缩规则与模板
- `references/interview-qa.md` — 面试问答预测标准分节与高危追问识别
- `references/export-templates.md` — 5 格式 × 4 模板导出细则
- `references/privacy-redaction.md` — 分享/导出前的隐私脱敏规则
- `templates/{professional,modern,minimal,academic}.html` — 4 份完整可填充 HTML 模板
- `examples/` — 样例输入简历 + 期望 diagnosis 结构（回归对照）

## 完整示例

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD
→ Step1 确认身份与目标 → Step2 评分（before 68/C，内容 18/30 无量化、ATS 8/15 关键词缺失、影响力 4/10 首屏无价值主张）+ 三标准判定（首屏❌ / 经历⚠️ / 匹配度❌）→ Step3 JD 拆硬要求+加分项、差距矩阵匹配度 55%、HR 视角扫出关键词缺失与硬伤、红旗标注"两段经历写成一样" → Step4 STAR 重写、强动词、补关键词、按目标岗重排，产出 `resume.md`（含详尽/标准/一行三版本）→ Step5 选 modern 模板导出 `resume.html` → Step6 **实际重跑评分**（after 89/B+，+21，diagnosis 含 before/after 对照表）+ 询问是否压缩一页 + 针对JD硬要求生成 `resume/interview-qa.md`。

无 JD 示例：用户只附简历无 JD → Step2 评分 → Step3 跳过（diagnosis 标注「通用优化模式」），不生成 `jd-analysis.md` → Step4-6 同上。
