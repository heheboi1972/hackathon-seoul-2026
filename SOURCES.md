# 저장소 자료 목록

## 원본 챌린지 자료

| 저장소 경로 | 자료 | 사용 목적 |
|---|---|---|
| `docs/sources/GWDC_Korea_Hackathon_FuriosaAI_X_Bricksum.pdf` | FuriosaAI × Bricksum Challenge Brief 원본 | AI 금융 서비스의 Kiln, 블록체인, 사용량, 두 번의 조건 검증 요구 확인 |
| `docs/sources/GWDC_Korea_Hackathon_TRON_Challenge_Brief.pdf` | TRON Challenge Brief 원본 | Energy 가격 비교, 자산 배분, GasFree 대량 결제 챌린지의 참고 범위 확인 |
| `docs/sources/GWDC.txt` | 사용자가 추가한 한국어 요약 | 팀이 읽기 쉬운 해커톤·트랙 요약. 평가 기준은 원본 PDF를 우선 |

## 프로젝트 실행·협업 문서

| 저장소 경로 | 설명 |
|---|---|
| `README.md` | 프로젝트 개요, 선택 기능, 담당자, 시작 문서 링크 |
| `TEAM_PLAN.md` | 시우·윤석·민진·민규 담당과 N-1부터 N-18까지 의존관계/완료 증거 |
| `PROJECT.md` | 사용자 흐름, 제품 범위, 공통 데이터/API 방향, 완료 기준 |
| `CONTRACTS.md` | API·타입·Protocol·경로 소유권의 단일 기준 |
| `AGENTS.md` | 저장소 작업 규칙, 테스트 명령, 보안·보고 조건 |
| `ROLE_BACKEND_AGENT.md` | 윤석: FastAPI·AI agent·승인 orchestration 작업 명세 |
| `ROLE_FRONTEND.md` | 민진: 사용자 UI·API 연결 작업 명세 |
| `ROLE_POLICY_BLOCKCHAIN.md` | 시우: 정책 엔진·감사 hash·testnet 작업 명세 |
| `ROLE_DATA_INTEGRATION_QA.md` | 민규: 가상 상품·simulator·QA 작업 명세 |

원본 PDF와 사용자가 제공한 GWDC.txt를 보존했다. 원본 챌린지 기준에서 Kiln 모델 요구사항은 `gpt-oss-120b`이므로 오래된 설계 문서의 잘못된 `Qwen3-32B` 표기를 바로잡았다. 운영진이 제공하는 실제 `KILN_MODEL` 식별자, API 접속 방법, 허용 testnet은 실연동 전에 확인해야 한다.
