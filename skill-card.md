## Description: <br>
求职者简历评分诊断 + 落地引擎。100 分制评分（5 维度 + A+~F 等级），40+ 项审计清单，STAR 法则量化改写，强动词替换，目标 JD 差距分析矩阵 + 匹配度，ATS 友好性检查，HR 6 秒筛选视角反向校验，红旗识别（外包/玩具项目/跳槽/空窗），多格式导出（HTML/Markdown/LaTeX/PDF/Word × 4 模板），重写后再次评分验证提升，一页简历压缩，生成面试问答。融合 taxue-career-resume、resume-helper、resume-optimizer-hr、resume-assistant、resume-optimizer 五者优点。 <br>

This skill is ready for commercial/non-commercial use. <br>

## Publisher: <br>
[zhugenmi](https://github.com/zhugenmi) <br>

### License/Terms of Use: <br>
MIT-0 <br>

## Use Case: <br>
求职者用于简历评分诊断、JD 分析（读懂目标岗位 + 差距矩阵）、HR 视角自审、STAR 重写、ATS 优化、红旗修复、多格式导出、一页压缩、面试问答预测。适用于"投了没回音"、应届生求职、换方向、晋升失败、外包/转岗/空窗期叙事修复等场景。仅面向求职者，不提供雇主侧写 JD / 筛选他人简历功能。 <br>

### Deployment Geography for Use: <br>
Global（中英文均可触发，中文 CJK 排版优化） <br>

## Known Risks and Mitigations: <br>
Risk: 重写时可能基于用户口述经历生成简历内容，存在美化或失真风险。 <br>
Mitigation: 重写必须基于用户提供的原始简历或项目经验；无真实数据时标注"待核实"占位符，不编造数字；用户应对最终简历真实性负责。 <br>
Risk: 评分为主观模型判断，可能与真实 HR 评价有偏差。 <br>
Mitigation: 评分维度与扣分原因全部透明列出，用户可对照自行校准；评分用于纵向对比提升而非绝对标准。 <br>
Risk: 导出 PDF 依赖用户浏览器手动操作，无法自动产出文件。 <br>
Mitigation: 明确告知导出步骤（Ctrl/Cmd+P → 另存为 PDF），HTML 已配置 `print-color-adjust: exact` 保证打印背景色。 <br>
Risk: 面试问答为基于简历与 JD 的预测，不代表真实面试题。 <br>
Mitigation: 仅作准备参考，标注为"预测问题"，建议结合目标公司面经使用。 <br>
Risk: JD 分析依赖用户提供的 JD 文本质量，可能误判硬要求。 <br>
Mitigation: 拆分硬要求/加分项时标注依据与不确定项，提示用户与招聘方确认。 <br>
Risk: ATS 兼容性建议基于通用规则，不同 ATS 系统行为有差异。 <br>
Mitigation: 建议使用标准标题与纯文本结构，避免表格/图片/文本框；关键岗位建议用目标公司指定渠道复核。 <br>

## Reference(s): <br>
- [taxue-career-resume（诊断来源）](https://github.com/taxueseek/taxueskills/tree/main/taxue-career-resume) <br>
- [resume-helper on ClawHub（执行来源，beikeliu）](https://clawhub.ai/beikeliu/skills/resume-helper) <br>
- [resume-optimizer-hr on ClawHub（STAR + ATS + 匹配度来源）](https://clawhub.ai/3492027682/skills/resume-optimizer-hr) <br>
- [resume-assistant on GitHub（100 分制评分 + 检查清单 + 多格式，Wscats）](https://github.com/Wscats/resume-assistant) <br>
- [resume-optimizer on GitHub（审计 + 红旗 + 一页压缩 + references 架构，wyh0626）](https://github.com/wyh0626/resume-optimizer) <br>

## Skill Output: <br>
**Output Type(s):** [Text, Markdown, HTML, LaTeX, Guidance] <br>
**Output Format:** [Markdown 评分诊断/JD 分析报告 + HTML/Markdown/LaTeX 简历 + Markdown 面试问答] <br>
**Output Parameters:** [1D] <br>
**Other Properties Related to Output:** [以 Markdown 为工作格式；HTML 简历供浏览器导出 PDF；评分报告、JD 分析、一页简历与面试问答落盘到 resume/ 目录。] <br>

## Skill Version(s): <br>
1.1.0 <br>

## Ethical Considerations: <br>
用户应评估本 skill 是否适合自身环境，使用前复核生成的简历与面试问答内容，不编造经历与数字，并在投递前按个人与组织的真实情况核对。简历涉及个人隐私信息，导出与分享时注意脱敏。评分仅作参考，不保证投递结果。 <br>
