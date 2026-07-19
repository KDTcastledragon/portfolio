# 작업 기록

## 2026-07-18 CastleChat 아키텍처 구분

- 기존 아키텍처 모달 안에서 On-Premise와 Cloud 배포 구조를 전환하도록 구성한다.
- On-Premise Nginx는 Windows native process, Cloud Nginx는 Kubernetes Pod의 container image로 구분한다.
- 기존 프로젝트 메뉴와 상세 모달을 재사용해 핵심 구현을 별도 항목으로 노출한다.
- On-Premise는 native Nginx, 5개 JVM process, Docker 기반 Kafka·Redis 구성을 표시한다.
- Cloud는 AWS Load Balancer, Kubernetes Cluster, Nginx Pod, 5개 application workload, stateful data workload를 표시한다.
- 기술 스택을 Client & UI, Service & Communication, Async Processing, Data & Cache, Infra & Monitoring으로 재분류했다.
- JavaScript 구문 검사는 `node --check`로 통과했다.

## 2026-07-19 CastleChat 아키텍처 시각 정리

- 서비스 구성은 유지하고 On-Premise 보드의 라벨, 연결선, 배경, 노드 간격만 정리한다.
- 환경 전환 버튼 외의 상단 정보와 하단 설명은 제거한다.
- NginX, Client, Redis, MariaDB 라벨을 단순화하고 연결선 위 텍스트를 모두 제거했다.
- 요청·응답은 양방향, Kafka publish·consume과 worker DB write는 단방향, Redis와 Gemini 호출은 양방향으로 다시 연결했다.
- 노드를 소폭 키우고 좌우 여백과 열 간격을 재배치했다.
- JavaScript 구문 검사는 `node --check`로 통과했다.

## 2026-07-19 CastleChat 기술 스택과 대표 화면 정리

- 기존 HTML/CSS 구조를 유지하고 기술 스택 가독성, 상세 항목 번호, Hero 장식만 최소 수정한다.
- 기술 스택 제목과 버전 요약을 제거하고 그룹명을 Front-End와 Server로 단순화했다.
- Async Processing과 Infra 설명을 짧게 정리하고 모달이 짧은 화면에서 내부 스크롤되도록 했다.
- 핵심 구현 6개와 트러블 슈팅 3개에 순번을 표시했다.
- 외부 이미지 없이 CSS 채팅 말풍선 일러스트를 Hero 우측 상단에 추가했다.
- JavaScript 구문 검사는 `node --check`로 통과했다.

## 2026-07-19 Cloud 아키텍처 단순화

- 첨부 도식에서 남긴 AWS 구성만 Cloud 탭에 재배치한다.
- 검게 지운 중간 구성은 요소와 여백을 함께 제거한다.
- AWS Cloud 안에 ECR, DEV VPC, EKS, MariaDB, S3를 배치하고 외부 Gemini와 Developer 흐름만 연결했다.
- ECR의 주황색 이미지 라벨을 CastleChat으로 표시했다.
- 기존 Load Balancer, Nginx Pod, 개별 서비스, Kafka, Redis, 모니터링 카드는 Cloud 패널에서 제거했다.
- 기존 모달 JavaScript 구문 검사는 `node --check`로 통과했다.

## 2026-07-13 랜딩 리디자인 (claude)

- 제목 재배치 : "멀티 프로세스 기반의"는 작은 도입 라인, h1은 "대규모 메시지 처리 지향 / 웹 채팅, CastleChat" 2줄 계층으로. 글자 수에 맞춰 폰트 축소(줄바꿈 깨짐 방지).
- 아키텍처 보기 : 페이지 이동 → 네이티브 dialog 모달로 전환. ESC 닫기(브라우저 기본) + 우측 상단 X + 배경 클릭 닫기.
- 버튼 배치 결정 : 배포 링크(+링크 복사)는 제목 바로 밑(첫 시선 = 체험 유도), 아키텍처 보기/기술 스택 보기는 우측 "설계 핵심" 패널 하단.
- 링크 복사 버튼 추가 : 클립보드 복사 + "복사 완료!" 피드백. 시범 URL https://www.naver.com (배포 링크 버튼도 동일 URL 새 탭).
- 기술 스택 보기 모달 추가 : Frontend(React 19.1, Redux Toolkit 2, TanStack Query 5, WebSocket) / Backend(Java 17, Spring Boot 3.5, gRPC 1.63, MyBatis, Write-Behind Flush Worker) / Data(Kafka, Redis, MariaDB) / Infra(Nginx, Docker, Prometheus, Grafana) 4그룹 카드.
- 용어 : dirty-flush-worker의 정확한 표현은 "Write-Behind Flush"(쓰기 지연 배치 반영)로 표기.
- 배포 시 실제 URL로 교체할 곳 : index.html의 DEPLOY_URL 상수 1곳 + 배포 링크 a href 1곳.

## 2026-07-16 CastleChat 섹션 콘텐츠 보강 (claude)

- hero 설명 문장 정리 : "연결 유지·검증·영속화 책임 분리 + 응답 경로에서 DB 대기 제거" 중심으로 재작성.
- 아키텍처 모달 각주 2→4개 : Process isolation(분리 기준), gRPC contract + shared session 추가. 각주 4칸 그리드 보더 규칙 수정(nth-child).
- 기술 스택 노트에 "왜" 보강 : Kafka(acks=all 후 응답), Redis(Lua 원자 병합·write-behind), gRPC(proto 계약), Flush Worker(N:1). Backend에 Snowflake ID 추가.
- 주요 스킬 개요 : placeholder → 설계 결정 카드 5개(Kafka 파이프라인, 읽음 write-behind, WS 멀티플렉싱, gRPC+세션 공유, 신뢰 경계·타입 모델링).
- 트러블 슈팅 : placeholder → 실제 사례 카드 3개(unread 부활 진단 스토리, prefix→ENUM 근본 수정, Redis/DB 불일치 보정). 진단/해결 뱃지(em) 스타일.
- detailDialog가 HTML 카드를 렌더하도록 변경(textContent→innerHTML, p→div). .detail-cards CSS 신설.
