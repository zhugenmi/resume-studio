# Sample Input: Foreign Enterprise (English)

> Regression reference: feed this resume to resume-studio (variant=foreign). Expected output structure in `expected-diagnosis-structure-foreign.md`.
> Redacted per `privacy-redaction.md`.

## Original Resume

```
Zhang San | Backend Engineer | 3 years experience
z***@example.com | Beijing | github.com/z***

Summary
Hardworking backend engineer who participates in team projects and is responsible for API development.

Experience
Company A — Backend Engineer (2022.06-Present)
- Responsible for backend API development
- Participated in database design
- Helped optimize interfaces
- Completed tasks assigned by manager

Project
E-commerce Backend System
- Responsible for product module
- Participated in order flow
- Did user management

Skills
Proficient in Java, Python, MySQL, Redis, Spring, Linux
```

## Target JD (excerpt)

```
Backend Engineer
- Required: Java/Go, MySQL, distributed systems fundamentals, Redis
- Bonus: Kubernetes, message queues, open-source contributions
```

## Expected Score Anchor

Per `scoring-rubric.md` Sample F (foreign variant weights), expected total ~**58/F**:
- Content 17/30: duty-layer bullets without results (-3 each), no quantification (-2 each).
- Structure 17/25: no value proposition in summary (-5), Chinese-style self-eval "hardworking" (-3).
- Language 12/22: bullets lack action verbs (-5), tense inconsistency (-3), "participated/did" weak verbs (-2).
- ATS 8/15: missing JD keywords K8s/message queue (-6), non-standard structure (-1).
- Impact 4/8: fails 6-second test (-3), no leadership evidence (-1).
- Red flags: "hardworking" Chinese-style self-eval (P1), bullets without action verbs (P1), summary not a value proposition.
