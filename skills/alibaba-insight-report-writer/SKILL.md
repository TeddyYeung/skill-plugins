---
name: alibaba-insight-report-writer
description: Translate and reconstruct overseas/domestic tech blog posts into Korean, McKinsey-style insight reports for both non-developers and developers. Use when asked to convert source articles into executive-ready documents with pyramid structure, MECE sections, glossary, architecture/flow visuals, actionable implications, Q&A, and quiz.
---

# Alibaba Insight Report Writer

Create high-signal Korean reports from external technical articles with executive readability and engineering rigor.
Default output location: `contents/tech-company-blogs/alibaba/`.

## Workflow

1. Define scope before writing.
- Set one `핵심 질문 (So what?)`.
- Define target audience (`경영진`, `PO/PM`, `개발팀`).
- Decide the expected decision outcome (adopt, pilot, hold, reject).

2. Extract only core signal from source.
- Capture thesis, 3-5 key insights, trade-offs, risks, and evidence.
- Avoid narrative filler and repeated examples.
- Keep factual claims source-traceable.

3. Translate and localize.
- Rewrite in natural Korean, not literal translation.
- Explain jargon once and reuse consistent terms.
- Keep English terms in parentheses at first mention.
- Maintain a glossary section.

4. Rebuild with McKinsey-style structure.
- Order: conclusion first, then 3 major evidence buckets, then details.
- Split sections using MECE (no overlap, no gaps).
- Include explicit business impact (cost, risk, speed, quality, customer impact).

5. Add mandatory visuals.
- Include at least:
  - architecture diagram
  - sequence/process flow
  - comparison table (`기존 vs 제안안` or `대안 A/B`)
- Add one-line caption under each visual (`이 슬라이드의 한 줄 메시지`).

6. Include audience-specific depth.
- Non-developer: translate to business language (time-to-market, risk, cost, productivity).
- Developer: include architecture decisions, trade-offs, limits, operational risks.
- Place detailed technical add-ons in appendix.

7. Verify before publish.
- Run dual review:
  - technical accuracy check
  - readability check for non-developers
- Confirm no mistranslation and that key message fits on one page.

## Required Document Skeleton

Use the structure in `references/report-template.md`.
Keep repository rule compatibility by including top-level `Question` and `Answer` before detailed sections.

## Fact vs Inference Rule

- Mark source-backed statements as `사실`.
- Mark author judgment as `해석`.
- For high-impact claims, add claim-to-source mapping in `근거/출처`.

## Output Quality Gate

The output is valid only if all are true:
1. Executive summary is readable in 60 seconds.
2. Core insights are grouped MECE with no duplicate points.
3. At least one architecture/process visual and one comparison table exist.
4. Q&A has 3-5 likely confusion points.
5. Quiz has 3-5 questions with answer and explanation.
6. Glossary includes key terms with English aliases.
7. Source links and publication dates are listed in appendix.

## Resource

- Template: `references/report-template.md`
