# HPDFS Portfolio Entry Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 프로젝트 번호 2를 실제 HPDFS 아키텍처와 FastAPI 및 PostgreSQL 기여가 드러나는 포트폴리오 사례로 교체한다.

**Architecture:** 기존 카드와 공용 상세 모달을 유지하고 `index.html`의 카드 마크업과 `projectDetails.smartctl` 데이터만 변경한다. 새 컴포넌트나 의존성 없이 기존 `detail-cards` 표현을 재사용한다.

**Tech Stack:** HTML5, CSS3, Vanilla JavaScript.

## Global Constraints

- 프로젝트 번호 2만 변경한다.
- 프로젝트 번호 3과 CastleChat 콘텐츠는 변경하지 않는다.
- 모델 관련 내용은 아키텍처와 기술 스택에만 표시한다.
- 개인 기여는 FastAPI와 PostgreSQL 설계로 제한한다.
- 기존 사용자 변경과 스타일을 보존한다.
- em dash 문자를 새 콘텐츠에 사용하지 않는다.

---

### Task 1: HPDFS 카드 교체

**Files:**
- Modify: `index.html:56`

**Interfaces:**
- Consumes: 기존 `.mini-project-card`, `.hero-description`, `.hero-actions`, `.mini-project-menu` 스타일.
- Produces: `data-detail="smartctl"`을 유지하는 HPDFS 프로젝트 카드.

- [ ] **Step 1: 프로젝트 카드의 현재 텍스트를 확인한다**

Run: `rg -n "SMARTCTL 분석 프로그램|data-detail=\"smartctl\"" index.html`

Expected: 프로젝트 번호 2 카드와 `projectDetails.smartctl` 위치가 출력된다.

- [ ] **Step 2: 카드 콘텐츠를 HPDFS로 교체한다**

카드 제목은 `HPDFS`, 설명은 `SMART 기반 저장장치 고장 예측 및 모니터링 시스템`, 담당 영역은 `FastAPI API 설계 · PostgreSQL DB 설계`로 표시한다. 상세 버튼 네 개는 `아키텍처`, `기술 스택`, `핵심 구현`, `트러블 슈팅`으로 구성한다.

- [ ] **Step 3: 카드 범위를 확인한다**

Run: `rg -n "HPDFS|FastAPI API 설계|가스 누출 방지" index.html`

Expected: HPDFS 콘텐츠와 변경되지 않은 가스 누출 카드가 함께 출력된다.

### Task 2: HPDFS 상세 콘텐츠 교체

**Files:**
- Modify: `index.html:655`

**Interfaces:**
- Consumes: `projectDetails`, `detailTypeLabel`, `.detail-cards`.
- Produces: `architecture`, `stack`, `core`, `trouble` HTML 템플릿.

- [ ] **Step 1: 아키텍처와 기술 스택을 시스템 전체 관점으로 작성한다**

아키텍처에는 Agent, Nginx, FastAPI, 예측 판정, PostgreSQL, Streamlit 흐름을 표시한다. 기술 스택에는 FastAPI, Pydantic, SQLAlchemy, PostgreSQL, Pandas, scikit-learn, RandomForest, joblib, Streamlit, Nginx, Docker Compose, Kubernetes, EKS, ECR을 역할별로 표시한다.

- [ ] **Step 2: 개인 기여를 백엔드와 DB로 제한한다**

`core`에는 요청 계약, 세션 관리, 이중 테이블, 시리얼 기준 갱신, 조회 및 조치 API, 수동 진단 저장 제외를 작성한다.

- [ ] **Step 3: 트러블 슈팅을 백엔드 및 DB 문제로 제한한다**

`trouble`에는 누적 이력과 최신 상태 분리, 반복 진단 중복 방지, 수동 데이터 격리, 세션 생명주기 관리를 작성한다.

- [ ] **Step 4: 모델 기여 과장을 검사한다**

Run: `rg -n "데이터 분석|모델 학습|전처리 담당|학습 담당" index.html`

Expected: 개인 기여와 트러블 슈팅 콘텐츠에서 해당 표현이 출력되지 않는다.

### Task 3: 구조와 인터랙션 검증

**Files:**
- Test: `index.html`

**Interfaces:**
- Consumes: 브라우저 기본 dialog API와 기존 이벤트 핸들러.
- Produces: 네 상세 버튼이 공용 모달에 올바른 콘텐츠를 표시하는 동작.

- [ ] **Step 1: HTML 파서를 실행한다**

Run: `python -c "from html.parser import HTMLParser; from pathlib import Path; HTMLParser().feed(Path('index.html').read_text(encoding='utf-8')); print('HTML parse OK')"`

Expected: `HTML parse OK`.

- [ ] **Step 2: JavaScript 구문을 검사한다**

Run: `node --check index.html`

Expected: HTML 파일 직접 검사가 지원되지 않으면 script 블록을 추출해 `node --check`를 실행하고 오류가 없어야 한다.

- [ ] **Step 3: 금지 문자와 대상 범위를 검사한다**

Run: `rg -n "—|SMARTCTL 분석 프로그램|data-detail=\"gas\"" index.html`

Expected: 새 HPDFS 콘텐츠에 em dash와 이전 제목이 없고, `data-detail="gas"`는 유지된다.

- [ ] **Step 4: 브라우저에서 프로젝트 2와 네 상세 메뉴를 확인한다**

Expected: 카드가 기존 레이아웃을 유지하고 네 버튼이 각각 올바른 제목과 콘텐츠를 표시한다.
