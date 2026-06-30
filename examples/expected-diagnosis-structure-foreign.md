# Expected diagnosis structure — foreign variant (regression reference)

> Feed `sample-input-foreign.md`; `resume/resume-diagnosis-foreign.md` must contain the structure below. Output in English by default.

## Required sections

### 1. One-line verdict (30-second read)
- Variant label: "Diagnosis variant: Foreign Enterprise (foreign)".
- One conclusion + grade + most fatal issue.

### 2. Score overview (before, foreign weights)
- Total + grade (foreign weights: content 30 / structure 25 / language 22 / ATS 15 / impact 8).
- Five-dimension breakdown + deduction reasons.
- Top 3 fatal issues.

### 3. Three core standards
- Value proposition in summary / bullets = action + quantified result / 6-second match.

### 4. Eight-category audit + foreign-specific items
- foreign-specific: full English / no photo-age-gender-marital / action-verb bullets / 1 page / quantified achievements / no Chinese-style self-eval / leadership evidence.

### 5. Red flags (foreign-specific)
- Chinese-style self-eval "hardworking" (P1 triggered), bullets without action verbs (P1 triggered), summary not a value proposition.

### 6. JD analysis + gap matrix
- Hard requirements per foreign context: Java/MySQL/distributed/Redis, bonus K8s/message queue.
- Match rate <60% expected.

### 7. Revision strategy + before/after example

### 8. Rewritten version (points to resume-foreign.md)

### 9. Verification score (after, foreign weights, actual rerun)

### 10. Next-step action checklist

## Required output files

- [ ] `resume-foreign.md` (three length variants)
- [ ] `resume-diagnosis-foreign.md` (before/after, foreign weights)
- [ ] `resume-foreign.html` (foreign template, English)
- [ ] `interview-qa-foreign.md` (English)
- [ ] `jd-analysis-foreign.md` (JD provided, required)

## Anti-patterns to avoid

- ❌ Scoring with soe or internet weights.
- ❌ Cross-variant before/after comparison.
- ❌ Missing variant label in diagnosis.
- ❌ Chinese characters in foreign-variant output (unless user explicitly switched to Chinese).
