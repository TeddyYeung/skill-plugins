---
name: gitbook-push-detailed-code
description: Publish markdown documents to GitBook (git-synced mode) with correct section routing, path updates, SUMMARY index updates, and push reporting. Use when asked to push/post docs to GitBook and when the output must contain highly detailed, concrete, executable code examples.
---

# Gitbook Push Detailed Code

Publish docs to GitBook with deterministic repository steps and enforce a strict detailed-code-example quality bar.
Default output is a markdown document plus an updated `SUMMARY.md`.

## Workflow

1. Define scope first.
- Set `핵심 질문(So what?)` and target audience.
- Confirm source links and publication dates.

2. Select GitBook section.
- Run section suggestion:
  - `python3 .codex/skills/gitbook-summary-publisher/scripts/suggest_gitbook_section.py --title "<title>" --text "<summary>"`
- If confidence `< 0.55`, request confirmation.

3. Write document using required structure.
- Follow `references/gitbook-report-template.md`.
- Separate `사실(출처)` and `해석(판단)`.
- Add at least one table and one diagram.

4. Enforce detailed code examples.
- Follow `references/detailed-code-example-checklist.md`.
- Never provide pseudo-only snippets for implementation sections.

5. Publish to GitBook repo (git-synced).
- Clone or pull target GitBook repository.
- Create/update markdown at routed path.
- Update `SUMMARY.md` in the corresponding section.
- Commit with:
  - `docs(<section>): add <short-title>`
- Push to remote branch.

6. Report result.
- Before push, report:
  - 추천 섹션
  - 예상 경로
  - 신뢰도
  - 대안 섹션
- After push, report:
  - 반영 파일
  - 커밋 SHA
  - 푸시 브랜치
  - 요약 포인트
  - 출처

## Detailed Code Policy

Apply all rules below whenever code examples are requested:
- Include full file context: file path, imports, classes/functions, and wiring code.
- Include runtime context: required package versions, env vars, execution command.
- Include concrete I/O: sample request/response, input/output JSON, expected logs.
- Include edge handling: retries, timeout, validation, error branch examples.
- Include verification: test command and at least one expected assertion/output.
- Prefer minimal runnable examples over fragmented snippets.

## Publish Commands

Use non-interactive commands:
```bash
git clone <gitbook_repo_url> /tmp/gitbook-repo
cd /tmp/gitbook-repo
git pull --ff-only origin <branch>
# update markdown + SUMMARY.md
git add <doc_path> SUMMARY.md
git commit -m "docs(<section>): add <short-title>"
git push origin <branch>
```

## Quality Gate

The output is valid only if all are true:
1. Section routing and confidence are reported.
2. Document structure follows template.
3. Code examples satisfy the detailed-code checklist.
4. `SUMMARY.md` update is included when publishing.
5. Push report includes commit SHA and changed files.

## Resources

- Template: `references/gitbook-report-template.md`
- Checklist: `references/detailed-code-example-checklist.md`
