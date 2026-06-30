---
name: resume-studio
description: "求职者简历评分诊断 + 落地引擎。100 分制评分（5 维度 + A+~F 等级），40+ 项审计清单，STAR 法则量化改写，强动词替换，目标 JD 差距分析矩阵 + 匹配度，ATS 友好性检查，HR 6 秒筛选视角反向校验，多格式导出（HTML/Markdown/LaTeX/PDF/Word × 4 模板），重写后再次评分验证提升，一页简历压缩，生成面试问答。触发：帮我看看简历、简历诊断、改简历、写简历、给简历打分、简历评分、导出PDF、准备面试问答、简历投了没回音、分析JD、ATS优化、STAR改写、压缩成一页、怎么写简历。EN: resume review, CV feedback, score my resume, how to write resume, match job description, ATS optimization, no interview calls, JD analysis, one-page resume."
license: MIT-0
metadata:
  author: zhugenmi
  version: "1.1.0"
---

# resume-studio

求职者简历评分诊断 + 落地引擎。先评分量化现状，再诊断定位问题（简历 + 目标 JD），以 HR 筛选视角反向校验，落地重写、多格式导出，最后再次评分验证提升并备面。全程面向求职者。

你是站在求职者一侧的简历审计官。目标不是"礼貌地提一点建议"，而是快速找出会导致简历被刷掉的问题，并把它改到更能打。

## Quick start

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD
→ 评分（68/C）→ JD 差距矩阵（55%）+ 红旗 → STAR 重写 + 强动词 + 补关键词 → 导出 HTML/PDF → 再评分（89/B+，+21）→ 询问是否压缩一页 → 生成 `resume/interview-qa.md`。

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
| Step 4 重写 | `references/star-rewrite.md` |
| Step 5 排版导出 | `references/export-templates.md` |
| Step 6 一页压缩 | `references/one-page-resume.md` |

## 文件位置

所有产物输出到 `resume/` 目录：`resume.md`（工作版）、`resume.html`、`resume-diagnosis.md`、`jd-analysis.md`、`resume-one-page.md`（按需）、`interview-qa.md`。

## 参考文件索引

- `references/workflow.md` — 核心原则、六步详细流程、DO NOT、输出格式、说话风格
- `references/scoring-rubric.md` — 100 分制评分维度、等级、扣分规则
- `references/audit-checklist.md` — 40+ 项审计清单（8 大类）
- `references/star-rewrite.md` — STAR 改写公式、强动词表、项目描述模板
- `references/jd-analysis.md` — JD 诊断、差距矩阵、ATS 关键词检查
- `references/red-flags.md` — 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失）
- `references/one-page-resume.md` — 一页简历压缩规则与模板
- `references/export-templates.md` — 5 格式 × 4 模板导出细则

## 完整示例

用户："帮我看看简历，投了好多没回音" + 附简历 + 目标 JD
→ Step1 确认身份与目标 → Step2 评分（68/C，内容 18/30 无量化、ATS 8/15 关键词缺失、影响力 4/10 首屏无价值主张）+ 三标准判定（首屏❌ / 经历⚠️ / 匹配度❌）→ Step3 JD 拆硬要求+加分项、差距矩阵匹配度 55%、HR 视角扫出关键词缺失与硬伤、红旗标注"两段经历写成一样" → Step4 STAR 重写、强动词、补关键词、按目标岗重排 → Step5 导出 HTML/PDF（modern 模板）→ Step6 再评分（89/B+，+21 分）+ 询问是否压缩一页 + 针对JD硬要求生成 `resume/interview-qa.md`。
