# PolicyGuard — GWDC Korea Hackathon

**선택 기능 선언:** 사용자가 정한 예산·허용 범위 안에서 상품을 추천하고, 정책을 통과해 사용자가 승인한 모의 구매만 실행한 뒤 근거를 테스트넷에 기록하는 AI 구매 에이전트.

> **모델 설정:** 사용자 결정에 따라 프로젝트는 Kiln의 **Qwen3-32B**를 사용하도록 계획합니다. 다만 첨부된 FuriosaAI 챌린지 원문에는 `gpt-oss-120b` 실호출 요구가 있으므로, Qwen3-32B 사용이 허용되는지 운영진 확인이 필요합니다. 확인 전에는 해당 모델 요건을 충족했다고 표시하지 않습니다.

FuriosaAI × Bricksum Challenge A의 금융 서비스 기능으로 준비하는 4인 팀 설계 저장소다. 실제 구현이 시작되기 전이며, 체크리스트와 단계는 계획이다. 이 MVP는 실제 쇼핑몰 주문이나 실제 금전 결제를 하지 않는다.

## 핵심 동작

1. 사용자의 자연어 요청에서 상품 조건 초안을 만든다. 누락·모호한 조건은 질문한다.
2. 사용자가 정책 조건을 확인한다.
3. 가상 상품을 검색해 추천하고, 서버 정책 엔진이 예산·판매처·카테고리·배송 기한·재고를 독립 검사한다.
4. 사용자가 최종 승인한 경우에만 서버가 재검사 후 모의 구매 영수증을 만든다.
5. 승인·정책·상품·모의 구매 기록의 해시를 testnet에 남기고 실제 TX receipt를 확인한다.

LLM은 조건 초안·추천 설명만 맡는다. 승인 권한, 가격 산정, 정책 허용/차단, 구매 중복 방지는 결정적 코드와 서버가 담당한다. 프로젝트 목표 모델은 Kiln의 `Qwen3-32B`다. 정확한 API model ID와 접속 방법은 운영진 가이드에서 확인하고, 원문 요구와의 차이는 별도로 허용 여부를 확인한다.

## 담당자와 첫 단계

| 담당 | 역할 | 시작 단계 |
|---|---|---|
| 시우 | Policy / Blockchain | 2-1 / P0: 정책 엔진·경계 테스트 |
| 윤석 | Backend / AI Agent | 1-2 / B0: 공통 타입·API 계약·서버 골격 |
| 민진 | Frontend | 2-3 / F0: 계약 타입·mock UI |
| 민규 | Data / Integration / QA | 2-2 / D0: 상품 fixture·검색·simulator |

1-2가 완료되면 시우·민진·민규의 기반 구현을 병렬로 시작한다. 작업 ID별 상세 의존성·인수 기준은 [TEAM_PLAN.md](TEAM_PLAN.md)에 있다.

## 문서 읽는 순서

1. [TEAM_PLAN.md](TEAM_PLAN.md) — 역할, 1-1~4-5 단계와 선행 조건
2. [PROJECT.md](PROJECT.md) — 제품 범위·사용자 흐름
3. [AGENTS.md](AGENTS.md) — 저장소 규칙·보안·검증 방법
4. [CONTRACTS.md](CONTRACTS.md) — API·공통 타입·파일 소유권
5. 담당 역할 문서 — [윤석](ROLE_BACKEND_AGENT.md) · [민진](ROLE_FRONTEND.md) · [시우](ROLE_POLICY_BLOCKCHAIN.md) · [민규](ROLE_DATA_INTEGRATION_QA.md)
6. [SOURCES.md](SOURCES.md) — 업로드한 원본·설계 자료 목록

## 자료

- `docs/sources/`에는 사용자가 추가한 FuriosaAI × Bricksum 원본 PDF, TRON Challenge 원본 PDF, `GWDC.txt`를 보존한다.
- TRON 자료는 별도 챌린지 참고용이며 현재 MVP 범위는 FuriosaAI 구매 에이전트다.
- 사용자의 최신 결정에 따라 프로젝트 모델을 `Qwen3-32B`로 설정했다. 첨부된 챌린지 원문은 `gpt-oss-120b`를 명시하므로, Qwen3-32B 사용 가능 여부를 운영진에게 확인해야 한다.
- API 키, RPC 비밀값, 테스트 지갑 개인키는 Git에 올리지 않는다. `.env.example`에는 변수 이름과 설명만 둔다.

## 현재 저장소 상태

현재 커밋에는 기획·설계·협업 문서만 있다. 앱 코드, Kiln 실호출, 테스트넷 TX, 실행 가능한 테스트 결과는 아직 없다. 각 작업 완료 후 실제 변경 파일·명령·통과/실패·mock/live 상태와 증거를 담당 ROLE 문서에 보고한다.
