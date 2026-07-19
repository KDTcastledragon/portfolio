# HPDFS 포트폴리오 항목 설계

## 목표

포트폴리오 두 번째 페이지의 프로젝트 번호 2를 HPDFS 사례로 완전히 교체한다. 채용 담당자가 첫 화면에서 시스템 목적과 개인 기여를 구분해서 이해하고, 상세 메뉴에서 FastAPI 및 PostgreSQL 설계 역량을 확인할 수 있게 한다.

## 범위

- `index.html`의 프로젝트 번호 2 카드만 변경한다.
- 프로젝트 번호 3인 가스 누출 방지 시뮬레이션은 변경하지 않는다.
- 기존 포트폴리오의 색상, 레이아웃, 모달 인터랙션은 유지한다.
- HPDFS 프로젝트의 실제 코드로 확인한 내용만 사용한다.
- 데이터 분석과 모델 학습은 아키텍처와 기술 스택에서만 시스템 구성요소로 소개한다.
- 개인 기여와 트러블 슈팅에는 데이터 분석 및 모델 학습 내용을 넣지 않는다.

## 카드 구성

- 프로젝트명은 `HPDFS`로 표시한다.
- 설명은 `SMART 기반 저장장치 고장 예측 및 모니터링 시스템`으로 정리한다.
- 담당 영역은 `FastAPI API 설계 · PostgreSQL DB 설계`로 명시한다.
- 종료된 AWS 배포 링크 대신 GitHub 저장소 링크를 제공한다.
- 상세 메뉴는 `아키텍처`, `기술 스택`, `핵심 구현`, `트러블 슈팅`으로 구성한다.

## 상세 콘텐츠

### 아키텍처

`Local Agent → Nginx → FastAPI → ML 및 SMART 규칙 판정 → PostgreSQL → Streamlit` 흐름을 역할별 카드로 설명한다. 로컬 하드웨어 접근이 필요한 Agent와 서버 영역이 분리되어 있다는 점을 명확히 한다.

### 기술 스택

- Backend 및 DB는 FastAPI, Pydantic, SQLAlchemy, PostgreSQL을 표시한다.
- 예측 구성요소는 Pandas, scikit-learn, RandomForest, joblib, SMART 규칙을 표시한다.
- Client 및 UI는 Python Agent, smartctl, Streamlit을 표시한다.
- Infra는 Nginx, Docker Compose, Kubernetes, EKS, ECR을 표시한다.

### 핵심 구현

- Pydantic `SmartData`를 이용한 진단 요청 계약.
- `Depends(get_db)`를 이용한 요청 단위 SQLAlchemy 세션 관리.
- `diagnosis_log` 누적 이력과 `disks` 최신 상태 분리.
- 디스크 시리얼 기준 insert 또는 update 처리.
- 전체 목록, 상세 이력, 조치 상태 변경 API.
- 수동 진단 결과의 운영 DB 저장 제외.

### 트러블 슈팅

- 진단 이력 누적과 최신 상태 조회 요구를 두 테이블로 분리.
- 동일 디스크의 반복 진단으로 생길 수 있는 중복 행을 시리얼 기준 갱신으로 방지.
- 수동 테스트 데이터가 운영 목록에 섞이지 않도록 저장 조건 분리.
- API 요청마다 DB 세션을 열고 `finally`에서 반환하도록 생명주기 관리.

## 디자인 기준

- 기존 포트폴리오 스타일을 보존하는 targeted evolution으로 진행한다.
- `DESIGN_VARIANCE 6`, `MOTION_INTENSITY 4`, `VISUAL_DENSITY 5`를 적용한다.
- 새 라이브러리와 새 모달은 추가하지 않는다.
- 기존 `detail-cards` 컴포넌트를 재사용한다.
- 프로젝트 카드와 상세 콘텐츠에 em dash 문자를 사용하지 않는다.

## 검증 기준

- 프로젝트 번호 2가 HPDFS로 표시된다.
- 프로젝트 번호 3은 변경되지 않는다.
- 네 개 상세 메뉴가 모두 해당 콘텐츠를 연다.
- 개인 기여 콘텐츠에 데이터 분석 또는 모델 학습 담당 표현이 없다.
- HTML 태그와 JavaScript 템플릿 리터럴이 정상적으로 닫힌다.
- 데스크톱과 모바일에서 기존 레이아웃 구조를 유지한다.
