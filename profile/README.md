# Serni

버추얼과 실시간 음성 대화를 지원하는 AI봇을 만듭니다.

## Serni란?

Serni는 사용자가 원하는 캐릭터와 자연스럽고 지속적으로 대화할 수 있는 AI 경험을 만드는 서비스입니다.

- **아바타 제작** — 이미지 한 장으로 버추얼 아바타를 만듭니다
- **AI봇** — 만든 아바타로 동작하는 텍스트·음성 대화 봇
- **리모트 컨트롤** — 원격 화면·인증·제어를 포함한 리모트 컨트롤

## 아키텍처

App(Electron)에서 Supabase로 직접 연결하고, 서버 작업은 Edge Functions에서만 처리하는 서버리스 구조입니다.

- **App** → Supabase 직접 (Auth · DB · Storage · Realtime)
- **Edge Functions** — `chat` · `deduct-token` · `toss-payment` · `avatar-generate`
- **토큰 경제** — 1토큰 = 1원, 초기 무료 300토큰

## 레포 구성

| 레포 | 역할 |
|------|------|
| `policy` | 사업 정책 + 공통 개발 룰 |
| `app` | Electron 앱 |
| `api` | Edge Functions (서버리스 API) |
| `server` | 로컬 STT/TTS 워커 |
| `avatar` | 아바타 제작·연구 |
| `cms` | 관리자 웹 |
| `website` | 서비스 소개 사이트 (serni.ai) |
| `remote` | 리모트 컨트롤 |
| `release` | 릴리스 관리 |

## 문서

- 사업 정책: https://docs.serni.ai
- 서비스: https://www.serni.ai

## 로드맵

- **S1** — 기본 AI 봇 (채팅·음성)
- **S2** — 토큰·DB·결제
- **B1 → B2** — 사업 검증

## 공통 개발 방식

공용 개발 정본은 [policy의 development 색인](https://github.com/Serni-Project/policy/blob/00fa48c5d72c323e6e348354b5ecf13d2dd877e2/development/README.md)입니다. 소비 저장소는 `.policy`로 이 커밋을 고정하고, 해당 파일을 직접 읽습니다. 사업 조건은 [사업 HTML](https://docs.serni.ai/)과 [에이전트 색인](https://docs.serni.ai/llms.txt)에서 확인합니다.

새 TODO 등록은 밥알이 담당합니다. 작업 중 우려사항은 이슈 댓글로 기록합니다. 완료되면 커밋 해시를 댓글로 남기고 resolve(close)합니다. AI가 산출물과 검사를 확인한 뒤 DONE 라벨을 붙입니다. 세부 기준은 [이슈 작업 단계](https://github.com/Serni-Project/policy/blob/00fa48c5d72c323e6e348354b5ecf13d2dd877e2/development/governance/issue-workflow.md#프로젝트-보드의-작업-단계)를 따릅니다.
