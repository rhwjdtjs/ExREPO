# Project SUV
> UE5(C++) 기반 **리슨 서버 Co-op 생존/탈출 게임** (Steam 출시 목표)

<!-- (선택) 커버/트레일러/배지 -->
<!--
<p align="center">
  <img src="YOUR_COVER_IMAGE_URL" alt="Project SUV Cover" width="100%"/>
</p>

<p align="center">
  <a href="YOUR_STEAM_URL"><img src="https://img.shields.io/badge/Steam-Coming%20Soon-000000?style=for-the-badge&logo=steam&logoColor=white"/></a>
  <a href="YOUR_REPO_URL"><img src="https://img.shields.io/badge/GitHub-Repo-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>
-->

---

## 1) 게임 소개 (Overview)
**Project SUV**는 한 섬에 “실험체(플레이어)”를 투입해 좀비가 존재하는 환경에서 생존을 강요하는 설정의 **Co-op 생존/공포** 게임입니다.  
플레이어는 각자 분산 스폰된 뒤 아이템을 파밍하며 생존하고, 서로 합류해 **미션을 완료한 뒤 탈출**하는 것이 목표입니다.

- 분위기: 포스트 아포칼립스 / 공포 / 생존
- 핵심 루프: **스폰 → 파밍/생존 → 합류 → 미션 진행 → 탈출**
- 위협 요소: 좀비 AI, 소음 유발에 따른 어그로, 자원 고갈

---

## 2) 개발 목적 (Goals)
- UE5(C++) 멀티플레이 환경에서 **서버 권한(Server Authority)** 기반 동기화를 안정적으로 구성
- 리슨 서버 Co-op 구조에서 발생하는 대표 이슈(지연, 판정 불일치, 복제 타이밍)를 재현/분해/해결
- “플레이 루프(생존→미션→탈출)”가 명확히 동작하는 **출시 가능한 데모 품질** 확보

---

## 3) 주요 구현 기능 (Key Features)
### 멀티플레이/네트워크
- 리슨 서버 기반 Co-op 아키텍처
- Replication / RPC(Server, Client, Multicast) 기반 상태 동기화
- 서버 확정 판정(예: 피격/데미지/상태변화) 및 결과 복제

### 전투/생존
- 근접/총기 전투
- 총기 사용 시 **소음(Noise) → 좀비 어그로(Aggro)** 유발
- 플레이어 상태: 체력(HP), 피격, 사망
- 생존 자원: 허기/탈진(및 확장 가능한 스탯 시스템)

### AI (좀비)
- 기본 좀비 AI(탐지/추적/공격)
- 소음 기반 추적 로직(Alpha~MVP 구간에서 고도화)

### 인벤토리/아이템
- 인벤토리 및 아이템 파밍
- 아이템 버프/디버프 효과
- 총기 부착물(Attachment) 생성/장착

### 미션/탈출 루프
- 미션 진행 → 조건 달성 → 탈출 플로우
- UI/HUD(상태/미션/상호작용) 제공

---

## 4) 기술 스택 (Tech Stack)
- **Engine**: Unreal Engine 5 (C++)
- **Network**: Listen Server / Replication / RPC
- **Platform**: Steam 배포 목표 (Steam 빌드/배포 파이프라인 준비)
- **Collaboration**: GitHub + Git LFS + Issues/Projects

---

## 5) 개발 일정 (Public Roadmap)
> 아래 일정은 **2인 개발 기준의 목표 로드맵**이며, 실제 진행에 따라 스프린트 단위로 조정될 수 있습니다.

| 단계 | 기간 | 목표 산출물 |
|---|---:|---|
| Pre-Prod | 1주(~01.04) | GDD / 기술설계 / 역할분담 확정 |
| MVP-1 | 1주(~01.10) | 멀티플레이 플러그인 제작(1/5), 캐릭터 애니메이션 셋, 조준 로직, 사격/공격, 무기 컴포넌트 분할 |
| MVP-2 | 1주(~01.18) | 좀비 제작 및 좀비 AI 제작(기본 AI) |
| MVP-3 | 1주(~01.24) | 캐릭터(HP/피격/사망), 좀비(HP/피격/사망) |
| MVP-4 | 2주(~02.07) | 인벤토리/아이템, 캐릭터 상태효과(허기/탈진 등), 아이템 버프, 총기 부착물 생성 및 장착 |
| MVP-5 | 2주(~02.21) | 임시 테스트 및 버그 수정, 데모 버전 촬영, 후원 받기 |
| MVP-6 | 2주(~03.07) | 소음 어그로, 사운드 플레이 제작(좀비 AI 수정) |
| Alpha | 4주(~04.04) | 미션/탈출 플로우 기획·제작, UI/HUD, 밸런싱 1차, 플레이 테스트 및 2차 데모 촬영 |
| Beta | 4주(~05.02) | 버그픽스/최적화/사용성 개선, 스팀 빌드/배포 준비 |
| 출시 | 4주(~06.03) | 5/2 스팀 신청 및 배포(심사 약 1달 예상) |

---

## 6) 플레이/빌드 (Getting Started)
> 추후 데모 배포 시 상세화 예정

- Unreal Engine 버전: `UE 5.x`
- 플랫폼: `Windows`
- 실행/빌드:
  1) 프로젝트 클론 (Git LFS 포함)
  2) UE 에디터에서 `.uproject` 열기
  3) `Development Editor` 빌드 후 실행

---

## 7) 협업 규칙 (Contributing / Workflow)
- 브랜치 전략: `main`(안정) / `dev`(통합) / `feature/*`
- 이슈 트래킹: GitHub Issues (재현 절차/스크린샷/로그 포함)
- PR 규칙: 기능 단위 PR, 체크리스트(테스트/리플리케이션/리뷰) 통과 후 머지

---

## 8) 팀 (Team)
- 2인 개발
- 역할 분담 및 책임 범위는 Pre-Prod에서 확정 후 문서로 관리

---

## 9) 라이선스 (License)
- TBD
