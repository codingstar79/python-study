# CLAUDE.md

이 폴더의 Claude Code 세션에 적용되는 프로젝트 지침입니다.

## 언어

- **모든 답변은 한글로 작성합니다.** 코드, 커밋 메시지, 주석 등 대화 응답은 항상 한국어로 합니다.
- 코드 자체(변수명, 함수명)는 영문 관례를 따르되, 주석은 한국어로 작성합니다.

## 파일 생성 규칙

- **새로 만드는 파일은 파일명 끝에 `_new`를 붙입니다.** (확장자 앞에 추가)
  - 예: `app.ts` → `app_new.ts`, `README.md` → `README_new.md`

## 디자인 시스템

- **UI/HTML/PPT 등 모든 시각 산출물을 작성/수정하기 전에 반드시 `DESIGN.md`(Apple 디자인 시스템, getdesign 설치)를 참조하고** 컬러·타이포그래피·간격 토큰을 준수합니다. 하드코딩 대신 DESIGN.md의 토큰 값을 사용합니다.
  - **`DESIGN.md`가 없으면**: 작업을 중단하지 말고, "DESIGN.md 없음 — 기본 스타일로 진행"을 한 줄 알린 뒤 진행합니다 (skip). 토큰을 임의로 만들어내지 않습니다.
- 기존 Mythos 디자인 시스템 파일(`mythos-design-system_new.css`, `DESIGN_GUIDE_new.md`)을 다루는 경우에만 my-design 스킬의 규칙을 따릅니다.

## 개발 원칙

- 간단하고 명확한 해결책을 우선합니다 (KISS).
- 중복 코드는 공통 함수로 추출합니다 (DRY).
- 필요하기 전에 미리 만들지 않습니다 (YAGNI).
- 오류는 명시적으로 처리하며, 조용히 삼키지 않습니다.
- 시스템 경계(사용자 입력, 외부 API 응답)에서는 반드시 유효성을 검사합니다.

## 작업 방식

- 복잡한 기능 구현 전에 계획을 먼저 세우고 공유합니다. *(Plan 모드 권장)*
- **모든 코드 언어의 소스 파일을 작성/수정한 경우** code-reviewer agent를 실행합니다. 특정 언어를 명시하지 않아도 코드가 담긴 파일은 모두 대상입니다 (예: .py, .ts, .js, .sh, .c, .cpp, .go, .rs, .java, .kt, HTML/CSS/JS, .ipynb의 코드 셀 등). 예외: 순수 문서(.md, .txt)와 .ipynb의 마크다운 셀만 수정한 경우는 제외합니다.
- 테스트가 가능한 구조라면 새 기능에 대한 테스트를 함께 작성합니다.
- 여러 단계가 필요한 작업은 할 일 목록으로 진행 상황을 추적합니다.

### Plan 모드 및 서브에이전트 활용 가이드

- **Plan 모드**: 복잡한 기능, 리팩토링 시 Shift+Tab 또는 "/plan" 사용. 설계 계획 수립 및 사용자 합의 필요.
- **서브에이전트**: 
  - 코드 작성 후 무조건 `code-reviewer` agent 실행
  - 테스트 필요 시 `tdd-guide` agent로 테스트 가이드 요청
  - 보안 이슈가 있으면 `security-reviewer` agent 실행
  - independent 한 작업은 병렬 실행 권장

## 테스트 요구 사항

- **최소 80% 커버리지** 필수 (상세: /home/guru/.claude/rules/ecc/common/testing.md 참조)
- **TDD 의무화**: 테스트 먼저 작성 후 구현 (상세: /home/guru/.claude/rules/ecc/common/testing.md 참조)
- **3대 테스트 필수**: 유닛, 통합, E2E 테스트 모두 반드시 포함 (상세: /home/guru/.claude/rules/ecc/common/testing.md 참조)

> **상세 가이드**: `/home/guru/.claude/rules/ecc/common/testing.md`
> 프로젝트별 예외사항은 이 파일을 수정하세요.

## Git

- 커밋 메시지는 Conventional Commits 형식을 따릅니다: `<type>: <description>`
- 타입: feat, fix, refactor, docs, test, chore, perf, ci
- 사용자가 요청하기 전에는 임의로 커밋하거나 푸시하지 않습니다.
