# 작업 기록

## 2026-07-13 랜딩 리디자인 (claude)

- 제목 재배치 : "멀티 프로세스 기반의"는 작은 도입 라인, h1은 "대규모 메시지 처리 지향 / 웹 채팅, CastleChat" 2줄 계층으로. 글자 수에 맞춰 폰트 축소(줄바꿈 깨짐 방지).
- 아키텍처 보기 : 페이지 이동 → 네이티브 dialog 모달로 전환. ESC 닫기(브라우저 기본) + 우측 상단 X + 배경 클릭 닫기.
- 버튼 배치 결정 : 배포 링크(+링크 복사)는 제목 바로 밑(첫 시선 = 체험 유도), 아키텍처 보기/기술 스택 보기는 우측 "설계 핵심" 패널 하단.
- 링크 복사 버튼 추가 : 클립보드 복사 + "복사 완료!" 피드백. 시범 URL https://www.naver.com (배포 링크 버튼도 동일 URL 새 탭).
- 기술 스택 보기 모달 추가 : Frontend(React 19.1, Redux Toolkit 2, TanStack Query 5, WebSocket) / Backend(Java 17, Spring Boot 3.5, gRPC 1.63, MyBatis, Write-Behind Flush Worker) / Data(Kafka, Redis, MariaDB) / Infra(Nginx, Docker, Prometheus, Grafana) 4그룹 카드.
- 용어 : dirty-flush-worker의 정확한 표현은 "Write-Behind Flush"(쓰기 지연 배치 반영)로 표기.
- 배포 시 실제 URL로 교체할 곳 : index.html의 DEPLOY_URL 상수 1곳 + 배포 링크 a href 1곳.
