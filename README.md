# Resume Studio

一个面向求职者的简历评分诊断 + 落地引擎 Skill。

它专注做一件事：把普通、松散、偏职责型的简历，评分定位最致命的问题，重写成更有说服力的求职材料，导出多格式文件，并验证提升效果。

## 这个项目解决什么问题

- 帮你找出简历里最致命的问题，而不是泛泛而谈
- 把"负责了什么"改成"做成了什么"——用 STAR 法则 + 强动词 + 量化
- 根据 JD 调整关键词、项目重点和职业叙事，输出匹配度差距矩阵
- 检查 ATS 友好性，避免被系统初筛刷掉
- 以 HR 6 秒筛选视角反向校验自己的简历
- 100 分制评分量化基线，重写后再次评分验证提升
- 多格式导出（HTML / Markdown / LaTeX / PDF / Word × 4 模板）
- 在用户需要时生成一份压缩后的一页简历
- 识别外包经历、玩具项目、量化缺失、频繁跳槽、空窗期等常见风险

## 项目结构

```text
resume-studio/
├── README.md
├── LICENSE
├── SKILL.md
├── skill-card.md
├── agents/
│   └── openai.yaml
└── references/
    ├── scoring-rubric.md       # 100 分制评分维度、等级、扣分规则
    ├── audit-checklist.md      # 40+ 项审计清单（8 大类）
    ├── star-rewrite.md         # STAR 改写公式、强动词表、项目描述模板
    ├── jd-analysis.md          # JD 诊断、差距矩阵、ATS 关键词检查
    ├── red-flags.md            # 红旗识别（外包/玩具项目/跳槽/空窗/量化缺失）
    ├── one-page-resume.md      # 一页简历压缩规则与模板
    └── export-templates.md     # 5 格式 × 4 模板导出细则
```

## 核心原则

- **内容优先于排版**：PDF 复制可能失真，但拼写、术语、时间线、逻辑错误仍是硬伤。
- **不编造成果**：可重写表达、补齐结构，但绝不捏造项目背景、指标、头衔。缺失信息用占位符 `[量化指标待补：...]` 标记。
- **量化优先于形容**：把"负责、参与"拆成"做了什么产物 + 影响了谁 + 带来什么变化"。
- **岗位匹配优先于通用正确**：用户提供 JD 时一切围绕 JD 取舍，写成"这个岗位愿意约面"的版本。
- **评分要诚实**：不为讨好用户给虚高分——虚高分帮不了他过 HR 的 6 秒。

## 工作流程（六步闭环）

```
收集 → 评分诊断 → JD分析+筛选校验 → 重写 → 导出 → 验证+备面
```

1. **收集**：原始简历 + 目标 JD + 身份目标
2. **评分诊断**：100 分制评分（5 维度 + A+~F 等级）+ 30 秒初判 + 三标准 + 40+ 项审计清单
3. **JD 分析 + 筛选校验**：JD 诊断 + 差距矩阵（匹配度 %）+ HR 6 秒视角 + 红旗识别
4. **重写**：STAR 法则 + 强动词 + 关键词 + 项目上下文先行
5. **导出**：Markdown 工作格式 → HTML/PDF/LaTeX/Word（4 模板）
6. **验证 + 备面**：再次评分对比提升 + 一页压缩（可选）+ 面试问答预测

## 安装

### Claude Code

```bash
mkdir -p ~/.claude/skills
cp -r resume-studio ~/.claude/skills/
```

### Codex / OpenClaw

```bash
mkdir -p ~/.codex/skills
cp -r resume-studio ~/.codex/skills/
```

### 手动安装

把整个目录复制到你的 skills 目录中，至少保留：

- `SKILL.md`
- `references/`
- `agents/openai.yaml`（如使用 OpenAI 兼容 agent）

## 适合什么场景

- 社招技术岗简历优化
- 校招项目描述提炼
- 投递前按 JD 定制简历
- 把两页以上的旧简历压缩成一页版
- 面试前自查简历漏洞
- 外包经历、转岗经历、空窗期的叙事修复
- ATS 友好性检查

## 使用方式

可以显式调用：

```text
Use $resume-studio to score my resume and diagnose gaps against a senior backend JD.
```

也可以自然语言触发：

```text
诊断我的简历
我的简历有哪些问题
帮我看看简历，投了好多没回音
给我简历打个分
根据这个 JD 定制我的简历：[粘贴 JD]
用 STAR 法则改写我的项目经历
把简历压缩成一页
优化我的简历让它通过 ATS 筛选
```

## 输出位置

所有产物输出到 `resume/` 目录：

- `resume/resume.md` — Markdown 工作版
- `resume/resume.html` — HTML 版（可浏览器导出 PDF）
- `resume/resume-diagnosis.md` — 评分诊断报告
- `resume/jd-analysis.md` — JD 分析报告
- `resume/resume-one-page.md` — 一页简历（按需生成）
- `resume/interview-qa.md` — 面试问答预测

## 融合来源

本 skill 参考了以下开源 skill 的优点：

- [taxue-career-resume](https://github.com/taxueseek/taxueskills/tree/main/taxue-career-resume) — 诊断锐度、三标准、锐利话术
- [resume-helper (beikeliu)](https://clawhub.ai/beikeliu/skills/resume-helper) — HTML 排版与执行闭环
- [resume-optimizer-hr](https://clawhub.ai/3492027682/skills/resume-optimizer-hr) — STAR 法则、ATS、匹配度评分
- [resume-assistant (Wscats)](https://github.com/Wscats/resume-assistant) — 100 分制评分、检查清单、差距矩阵、多格式
- [resume-optimizer (wyh0626)](https://github.com/wyh0626/resume-optimizer) — 审计清单、红旗识别、一页压缩、references 路由架构
