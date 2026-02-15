# 다른 프로젝트로 옮겨서 바로 쓰는 가이드

## 1) 이 프로젝트에서 옮길 파일

아래 파일들을 **세트로** 복사하세요.

- `AGENTS.md`
- `create-prd.md`
- `generate-tasks.md`
- `PROMPT-START.md`
- `docs/project-brief.md`
- `docs/tech-context.md`
- `docs/conventions.md`
- `docs/decision-log.md`

권장: 대상 프로젝트에도 `tasks/` 폴더를 미리 만들어 두세요.

---

## 2) 대상 프로젝트에서 기본 세팅

1. 위 파일들을 대상 프로젝트 루트에 붙여넣기
2. 아래 파일부터 채우기
   - `docs/project-brief.md` (필수)
   - `docs/tech-context.md` (권장)
   - `docs/conventions.md` (권장)
3. `tasks/` 폴더가 없으면 생성

예시:

```bash
mkdir -p tasks docs
```

---

## 3) Codex에 초안(PRD + 작업계획) 생성시키는 방법

### 방법 A: 가장 빠른 방법 (권장)

`PROMPT-START.md` 내용을 그대로 복사해서 Codex에 입력하세요.

이렇게 진행됩니다:
1. `docs/project-brief.md` 기반으로 PRD 작성
2. `tasks/prd-[feature-name].md` 저장
3. Parent Tasks 제안 후 `"Go"` 대기
4. Sub-tasks + Relevant Files 제안 후 `"Approve files"` 대기
5. `tasks/tasks-[feature-name].md` 저장 후 구현 시작

### 방법 B: 수동 2단계

1) PRD 생성 요청

```text
Use @create-prd.md
Use this project brief: @docs/project-brief.md
Reference files: [@docs/tech-context.md @docs/conventions.md]
Save as /tasks/prd-[feature-name].md
```

2) Task 생성 요청

```text
Use @generate-tasks.md with @tasks/prd-[feature-name].md
Generate parent tasks first and wait for my "Go".
After sub-tasks and relevant files are drafted, wait for my "Approve files".
Save as /tasks/tasks-[feature-name].md
```

---

## 4) 실제 실행 규칙 (진행 중)

- Codex가 각 sub-task 완료 시 `tasks/tasks-[feature-name].md` 체크박스를 업데이트하도록 유지
- 구현 중 중요한 선택은 `docs/decision-log.md`에 기록
- 범위 변경이 생기면 먼저 `docs/project-brief.md`를 업데이트 후 계속 진행

---

## 5) 실패/막힘 방지 체크리스트

- `docs/project-brief.md`의 `In scope / Out of scope`가 비어있지 않은가?
- `Acceptance criteria`가 pass/fail 형태인가?
- 파일 경로가 실제 프로젝트 구조와 맞는가?
- `tasks/` 폴더가 존재하는가?
- Parent Tasks 승인(`Go`)과 File Plan 승인(`Approve files`) 단계를 지켰는가?

---

## 6) 최소 시작 템플릿

아래 한 줄로 시작해도 됩니다.

```text
프로젝트 계획 시작. PROMPT-START.md 절차대로 PRD와 Task 초안부터 만들어줘.
```

