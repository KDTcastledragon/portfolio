# Project Summary Modal Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 페이지네이션 옆에 프로젝트 참여 요약 버튼과 여섯 프로젝트 요약 모달을 추가한다.

**Architecture:** 기존 네이티브 dialog 및 공통 모달 이벤트를 재사용한다. 새로운 JavaScript 동작은 만들지 않고 HTML과 CSS만 추가한다.

**Tech Stack:** HTML5, CSS3, Vanilla JavaScript.

## Global Constraints

- 페이지네이션과 버튼의 데스크톱 간격은 100px이다.
- 개인 4개, 팀 2개로 표시한다.
- 닫기 버튼, 바깥 클릭, Esc 닫기를 지원한다.
- 기존 프로젝트 콘텐츠를 변경하지 않는다.

---

### Task 1: 트리거와 모달 마크업

**Files:**
- Modify: `index.html`

- [ ] 헤더에 `data-open="projectSummaryDialog"` 버튼을 추가한다.
- [ ] 여섯 프로젝트를 담은 전용 `<dialog>`를 추가한다.
- [ ] 기존 공통 모달 이벤트가 새 dialog를 처리하는지 확인한다.

### Task 2: 위치와 반응형 스타일

**Files:**
- Modify: `index.css`

- [ ] 데스크톱에서 페이지네이션 오른쪽 100px 간격을 적용한다.
- [ ] 요약 모달을 2열 카드로 구성한다.
- [ ] 모바일에서 버튼 문구와 모달 카드를 축약 및 1열 처리한다.

### Task 3: 검증

- [ ] HTML 필수 요소와 JavaScript 구문을 검사한다.
- [ ] 브라우저에서 버튼, 모달, Esc 닫기를 검증한다.
- [ ] `git diff --check -- index.html index.css`를 통과한다.
