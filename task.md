# 작업 기록

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
