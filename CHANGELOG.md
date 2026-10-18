# 변경 이력

DungeonHelper Windows 배포 버전의 변경사항입니다. 최신 버전부터 정리합니다.

## [v1.1.5](https://github.com/supremiere/DH-releases/releases/tag/v1.1.5) — 2026-10-19

- 함께하기 입장 후 파티원이 부족할 때 표시되는 도전하기 버튼을 최대 5초 동안 확인하고, 발견하면 즉시 클릭합니다.
- 도전하기 이미지를 기존 입장 버튼과 같은 기준 배율 및 인식 방식으로 처리합니다.
- 혼자하기의 기존 입장 및 추가 입장 확인 흐름은 유지합니다.

## [v1.1.4](https://github.com/supremiere/DH-releases/releases/tag/v1.1.4) — 2026-10-18

### 물길 입구 보정 검증 반복 수정

- 추가 이동 검증이 반복해서 기존 측정과 맞지 않아도 앞선 두 축을 계속 고정하고 같은 방향만 재시도하던 문제를 수정했습니다.
- 한 번의 불일치에서는 해당 측정만 재시도합니다. 같은 검증 모순이 두 번 이어지면 앞선 축도 미확정으로 처리하고, 반대 옆 방향과 W부터 다시 측정합니다. 보정 중 S 입력 제외와 짧은 입력 상한은 유지합니다.
- 좌표·정지 정보가 부족한 일반 재시도는 기존처럼 정상 측정을 보존합니다. 로그에 기존 축을 폐기하고 재검증한 이유를 남깁니다.

제보 로그에서는 보정 시작부터 완료까지 약 90초 걸렸고 같은 A 검증 실패가 반복됐습니다. 이번 수정은 그 반복 경로를 보완한 것입니다. 최초 축이 왜 불일치했는지는 원시 좌표 자료가 없어 확정하지 않았으며, 모든 환경에서 보정 성공이나 근딜 회귀 해결을 보장하는 것은 아닙니다. 자동 시험과 Windows 패키지 검사를 수행했으며 수정 후 실전 재확인은 필요합니다.

## [v1.1.3](https://github.com/supremiere/DH-releases/releases/tag/v1.1.3) — 2026-10-18

### 물길 객체 식별·방향 보정과 재개 개선

- 입장 직후 오른쪽 ‘흩어진 물길 클리어’ 글자를 확인하면 투창병 등장 전 보정을 시작합니다. 투명한 패널 배경을 제외하고 글자를 비교하며, 다른 어비스 버튼과 같은 배율 탐색·세밀한 크기 보정·배율 및 위치 기억을 사용합니다. 창 크기나 위치가 달라지면 다시 확인합니다.
- 첫 보정 이동은 좌·우 중 무작위로 선택하고, 유지 시간도 0.45~0.65초로 다르게 정합니다. 앞뒤 축 측정에는 W를 사용하며 보정 중 S 입력은 제외합니다. 네 명이 항상 서로 다른 방향으로 갈 것을 보장하는 방식은 아닙니다.
- 관측한 플레이어 직업 스킬의 시전자와 실제 이동·정지 반응을 결합해 객체 후보를 좁힙니다. 미등록 직업은 기존 이동 검증 경로를 유지합니다.
- 보정이 실패하면 실패한 방향만 다시 측정하고 앞선 측정은 보존합니다. 두 번 실패해도 그 판을 포기하지 않고, 자동전투 ON 확인 후 3초 전투하고 보정을 재개합니다.
- 입구에서 보정이 완료된 뒤 이동/H/Q/E 입력에 양보하더라도 완료한 값을 유지합니다. 1번방 객체가 나중에 연결돼도 재사용하며 실제 시점 변경·수신 오류·새 입장 등의 초기화 조건은 유지합니다.

자동카메라 OFF와 Npcap 설치 조건은 유지합니다. 자동 시험과 Windows 패키지 실행 검사를 수행했습니다. r23 실전 로그에서 입구 보정 및 이후 1번방 적중 1회·종료가 기록됐지만, 그 사이 불필요한 재보정이 있어 최종 수정했습니다. **최종 수정 후 실제 근딜 회귀 해결 여부와 4인 동시 동작은 추가 확인이 필요합니다.** 3번방 O/X 자동 해결은 이번 배포에 포함하지 않습니다.

## [v1.1.2](https://github.com/supremiere/DH-releases/releases/tag/v1.1.2) — 2026-10-18

### 물길 창 대기와 막힘 복구 수정

- 투창병→같은 속성 주술사→내 캐릭터의 정렬이 확인되면 창을 기다립니다. 정렬된 자리에서 고정 목표점을 계속 쫓다가 막힘 복구로 넘어가는 경우를 보완했습니다.
- 정렬·적중 대기 중에는 자동전투 OFF를 유지합니다. 다른 파티원 조준이나 위치 확인 중단만으로 자동전투 ON을 허용하지 않습니다.
- 막힘 판정 뒤 늦게 들어온 좌표가 정렬을 보여주면 잡몹 정리를 취소합니다. 실제 막힘으로 정리를 예약했더라도 내 창 발사 확인과 기존 적중 판정 구간이 지나기 전에는 대상 변경·자동전투 ON을 시도하지 않습니다.
- Q/E 전송 기록과 실제 대상 변경·잡몹 처치 확인을 구분하도록 로그를 수정했습니다. 실제 게임에서 대상 변경과 잡몹 공격이 되는지는 추가 검증이 필요합니다.
- 초기 방향 보정을 짧게 하고 첫 두 방향도 무작위화했습니다. 추가 확인은 기본 1회이며 후보가 겹치면 최대 3회까지 확인합니다.

자동카메라 OFF와 Npcap 설치 조건은 유지합니다. 자동 테스트와 Windows 실행 검사를 진행했으며, 수정 후 실제 게임에서의 창 적중·잡몹 정리 재시험은 아직입니다.

## [v1.1.1](https://github.com/supremiere/DH-releases/releases/tag/v1.1.1) — 2026-10-18

### 물길 수신 복구 및 파티 캐릭터 식별 보완

- 수신 데이터의 도착 순서가 바뀌면 누락 구간을 기다려 재조립합니다. 복구 중 이동 키를 해제하고 기존 방·보정·적중 상태를 보존합니다.
- 복구한 좌표의 원래 수신 시각을 유지합니다. 손상되거나 끝내 복원할 수 없는 데이터는 임의로 해석하지 않고, 자동전투 ON을 확인한 뒤 새 연결 또는 확인된 세션 시작 경계를 기다립니다.
- W/D 보정 뒤 PC마다 다른 방향 순서와 유지 시간으로 짧은 확인 입력을 3번 추가합니다. 전체 입력에 일치하는 객체가 하나일 때만 내 캐릭터로 판단하며, 후보가 겹치면 임의 선택 없이 재측정합니다.
- 파티 화력으로 보정 중 1번방 몬스터가 처치되면 입력을 끝내고 자동전투로 복귀합니다.
- 로그에 수신 오류 이유, 수신·해석 횟수와 보정 후보 수를 남겨 실패 지점을 구분할 수 있도록 했습니다.

### 사용 조건과 검증 범위

**자동카메라 OFF와 Npcap 별도 설치가 필요합니다.** 물길을 선택하고 입장 전에 실행하세요. 첫 보정에는 짧은 확인 이동이 세 번 추가됩니다. 연결된 자동 기믹은 물길 1번방 창 기믹이며, 3번방 O/X 자동 해결은 포함하지 않습니다.

전체 자동 테스트 1,151개 통과, 2개 건너뜀 및 Windows 시험 패키지 시작·트레이 검사를 확인했습니다. 1~4개 클라이언트의 동시 보정 모의 시험과 기존 수신 기록의 순서를 뒤바꾼 재생 시험도 통과했습니다. **수정 후 실제 노트북·4인 파티 재시험은 아직이며, 이번 배포로 사례를 수집합니다.** 실제로 유실된 바이트를 복원하거나 동일하게 반응한 여러 객체를 무조건 구분할 수 있다는 뜻은 아닙니다.

문제가 생기면 [사례 제보](https://github.com/supremiere/DH-releases/issues)에 버전, 직업, 파티 인원·모드, 자동카메라 OFF 여부, 발생 시각과 해당 시간대의 `%APPDATA%\DungeonHelper\logs\abyss-detail.log`를 남겨 주세요. 개인 정보는 가려 주세요. 원시 패킷·개인 설정·시험 로그를 배포 파일에 넣거나 자동 업로드하지 않습니다.

## [v1.1.0](https://github.com/supremiere/DH-releases/releases/tag/v1.1.0) — 2026-10-18

### 흩어진 물길 1번방 자동 처리

- 내 캐릭터가 창 조준 대상일 때 수신 정보로 속성과 목표 주술사를 구분하고, 같은 표식의 주술사 뒤로 이동합니다.
- 1번방에서 W/D 방향을 자동 보정합니다. 창 패턴이 다시 나오면 갱신된 조준 정보로 반복 처리합니다.
- 몹에 막혀 이동이 원활하지 않으면 Q/E로 대상을 바꾸고 자동전투로 공격한 뒤 다음 조준에서 재시도합니다.
- 창 적중 근거와 자동전투 ON 복귀를 확인해 기믹을 집계합니다. 막힘 복구 직후의 같은 창 적중도 중복 없이 반영합니다.
- 직접 조작에는 입력을 양보하고, 카메라를 직접 돌리면 방향을 다시 보정합니다.

### 사용 전 확인

- **게임의 자동카메라 옵션을 OFF로 설정하세요.** 게임이 시점을 자동 변경하는 상황은 현재 자동 감지하지 못합니다.
- 물길 기믹 자동화에는 **Npcap이 별도로 설치되어 있어야 합니다.** 이번 ZIP에는 Npcap 드라이버/설치 파일을 포함하지 않습니다. 설치 파일은 [Npcap 공식 사이트](https://npcap.com/#download)에서 받으세요.
- 물길을 선택하고 던전에 들어가기 전에 실행하세요. 게임 창을 앞으로 두고, 방향 보정과 기믹 수행 중에는 이동·시점·H·Q·E 조작을 피하세요.
- 수신 준비에 실패하면 물길 기믹 자동 처리가 중단되고 상세 로그에 사유를 남깁니다. 기존 이미지 기반 던전·어비스 진행은 유지됩니다.
- 이번에 연결한 자동 기믹은 **1번방 창 기믹**입니다. 3번방 O/X 기믹 자동 해결은 포함하지 않습니다.

### 화면 배율 및 인식 개선

- ASSIST 상태 인식에서 확인한 위치와 배율을 재사용해 반복 탐색 비용을 줄였습니다. ON/OFF 상태는 매번 현재 화면으로 확인합니다.
- 던전햄순이에도 화면 배율을 표시합니다. 중지 상태에서 감지된 배율을 누르면 게임 창을 100% 기준 크기로 맞춥니다. 크기 변경 후 실제 인식으로 배율을 다시 확인합니다.
- 보스 컷씬 및 콤보 처리 중 게임 창의 포커스가 바뀌는 경우를 보완했습니다.

### 확인 범위와 사례 제보

원거리·근거리 캐릭터의 1번방 보정, 창 기믹 반복, 막힘 복구 후 다음 조준 처리와 방 종료를 시험했습니다. 자동카메라를 끈 뒤 근거리 캐릭터의 여러 판이 정상 동작했다는 사용자 확인도 받았습니다. 모든 직업·실제 4인 조합·장시간 전체 던전 반복을 보장하는 결과는 아닙니다. 복구 직후 적중 집계는 자동 테스트와 기존 수신 기록 재생으로 확인했으며 해당 분기의 추가 실전 사례를 수집합니다.

다양한 환경의 성공·실패 사례는 [공개 배포 저장소의 Issues](https://github.com/supremiere/DH-releases/issues)에 남겨 주세요. 다음 항목을 함께 적으면 원인 확인에 도움이 됩니다.

- 버전, 직업/근거리·원거리, 파티 인원과 실행 모드
- 자동카메라 OFF 여부, 게임 창 크기와 표시된 화면 배율
- 발생 시각, 멈춘 단계, 기대한 동작과 실제 동작
- 해당 시간대의 `%APPDATA%\DungeonHelper\logs\abyss-detail.log` 발췌

개인 정보가 있으면 가리고 공유하세요. 원시 패킷이나 로그를 자동 업로드하지 않습니다.

## [v0.7.21](https://github.com/supremiere/DH-releases/releases/tag/v0.7.21) — 2026-10-17

### 수정

- restart Abyss entry after reconnecting to Imemaha and preserve dungeon progress (`cbef3ec`)

### 기타

- release location-aware Abyss recovery as v0.7.21 (`9677df2`)

## [v0.7.20](https://github.com/supremiere/DH-releases/releases/tag/v0.7.20) — 2026-10-17

### 수정

- resume dungeon and Abyss loops five seconds after disconnect confirmation (`fcdbd1a`)

### 기타

- release fixed reconnect pause as v0.7.20 (`2b77158`)

## [v0.7.19](https://github.com/supremiere/DH-releases/releases/tag/v0.7.19) — 2026-10-17

### 수정

- dismiss disconnect popups throughout dungeon runs without resetting progress (`2210cb3`)

### 기타

- release dungeon popup recovery as v0.7.19 (`fd356aa`)

## [v0.7.18](https://github.com/supremiere/DH-releases/releases/tag/v0.7.18) — 2026-10-17

### 수정

- dismiss disconnect popups throughout party loops and resume current phase (`b5f4213`)
- enable popup guard for all Abyss roles without blocking capture (`cd688f6`)

### 기타

- release Abyss popup recovery as v0.7.18 (`9742c1e`)

## [v0.7.17](https://github.com/supremiere/DH-releases/releases/tag/v0.7.17) — 2026-10-17

### 수정

- recover server disconnects during leader entry preparation (`69cbd0d`)

### 추가

- add four-player leader in-dungeon retry mode (`449d2a9`)
- authorize special Discord users through existing remote D1 allowlist (`80f5805`)
- add isolated admin API for special Discord access management (`0eea6d0`)

### 기타

- release integrated changes as v0.7.17 (`d0d5f1a`)

## [v0.7.16](https://github.com/supremiere/DH-releases/releases/tag/v0.7.16) — 2026-10-16

### 수정

- 보스전 컷씬 스킵 이미지 인식 개선 (`93e44ac`)
- 보스전 오프닝 콤보 궁극기 사용 로직 개선 (`b00a1b0`)

### 기타

- 버전을 0.7.16으로 올림 (`1b4d5a5`)

## [v0.7.14](https://github.com/supremiere/DH-releases/releases/tag/v0.7.14) — 2026-10-10

### 수정

- preserve dungeon completion evidence independently of bag reads and logs (`1de1dea`)
- count the cleared dungeon before waiting for retry (`b636fd5`)

### 기타

- preserve original workflow line endings (`7492fae`)

## [v0.7.13](https://github.com/supremiere/DH-releases/releases/tag/v0.7.13) — 2026-10-09

### 수정

- 던전 구역을 층별로 합산하고 대시보드 판수를 실제 완료 기준으로 수정 (`7475a1e`)

## [v0.7.12](https://github.com/supremiere/DH-releases/releases/tag/v0.7.12) — 2026-10-09

### 수정

- AI 위치 판정과 선택 던전을 함께 사용해 완료 판수 분류 안정화 (`c121b00`)

## [v0.7.11](https://github.com/supremiere/DH-releases/releases/tag/v0.7.11) — 2026-10-04

### 수정

- 실행 중 인증을 통신 장애와 단기 만료에도 유지 (`7359602`)

## [v0.7.10](https://github.com/supremiere/DH-releases/releases/tag/v0.7.10) — 2026-10-04

### 기타

- Add one-time operator-approved historical abyss attribution (`0cdc1b0`)
- Classify confirmed pre-0.7.8 abyss clients as Harbor (`bfe6a97`)

### 수정

- limit followup backfill to the four approved runs (`600b1cc`)
- Discord 인증 갱신 일시 오류와 만료 복구 처리 (`3964256`)
- honour cancellation when automatic login retry fails (`2d23e6d`)

### 테스트

- make offline profile status deterministic (`10127a7`)

## [v0.7.9](https://github.com/supremiere/DH-releases/releases/tag/v0.7.9) — 2026-10-03

### 기타

- Add close-to-tray choice and use the existing hamster application icon (`96d09c6`)
- Exclude disconnected AI Connector users from shared statistics (`b5f0d02`)

## [v0.7.8](https://github.com/supremiere/DH-releases/releases/tag/v0.7.8) — 2026-10-03

### 기타

- Track known dungeon completions without resetting historical totals (`cac1b48`)

## [v0.7.7](https://github.com/supremiere/DH-releases/releases/tag/v0.7.7) — 2026-10-03

### 수정

- Windows 빌드 압축 해제 및 Discord 로그인 유지 (`640a450`)

## [v0.7.6](https://github.com/supremiere/DH-releases/releases/tag/v0.7.6) — 2026-10-03

### 추가

- collect per-dungeon completion and drop-hit rates (`c25c24c`)

## [v0.7.5](https://github.com/supremiere/DH-releases/releases/tag/v0.7.5) — 2026-10-03

### 수정

- preserve and recover combo presets across app updates (`38ea522`)

### 기타

- bump version to 0.7.5 for preset preservation fix (`7d465ed`)

## [v0.7.4](https://github.com/supremiere/DH-releases/releases/tag/v0.7.4) — 2026-10-03

### 추가

- add mandatory Discord identity and passive drop statistics (`e3229a8`)
- keep the mining hamster visible below navigation after login (`9141108`)
- deploy Discord identity and drop statistics API on Cloudflare (`8802b4b`)

### 수정

- dispose login windows safely and verify packaged auth startup (`7975d0a`)
- identify DungeonHelper explicitly in authentication API requests (`44e29bc`)
- Discord 로그인 연결과 프로필 사진 표시 수정 (`3a93154`)

### 기타

- Discord 인증 및 통계 배포 버전을 v0.7.4로 갱신 (`17a9d4e`)

## [v0.7.3](https://github.com/supremiere/DH-releases/releases/tag/v0.7.3) — 2026-10-03

### 수정

- 창 크기 유지와 입장·재입장 배율 보정 및 간식 오인식 검사 개선 (`7889cb1`)

### 기타

- 이미지 탐색과 창 크기 유지 수정에 맞춰 v0.7.3으로 버전 갱신 (`614b7e5`)

## [v0.7.2](https://github.com/supremiere/DH-releases/releases/tag/v0.7.2) — 2026-10-03

### 추가

- 전투 진입 60초와 재입장 준비 3분·2분 지역 감시 및 보조 상태 UI 개선 (`3c48f59`)

### 수정

- 보스 컷씬 원본 검증을 픽셀 단위로 보정해 중간 배율 감지 누락 해결 (`7281ea4`)

### 문서

- 지역 감시 기준과 해상도별 이미지 점검 결과 및 남은 문제 기록 (`a05b9a0`)

### 기타

- 지역 감시와 컷씬 감지 수정에 맞춰 v0.7.2로 버전 갱신 (`456c1b9`)

### 테스트

- 컷씬 검증 실패 진단에 맞춰 테스트 후보 배율 정보 보강 (`ff4bc1c`)

## [v0.7.0](https://github.com/supremiere/DH-releases/releases/tag/v0.7.0) — 2026-10-02

### 개선

- 완료 탐색 최적화와 부활 작업 분리 및 지역 복구 안정화 (`033cbf2`)

### 추가

- 어비스 진행 상태와 보조 작업 다섯 칸 UI 개선 (`a767fb6`)

### 기타

- 어비스 탐색 구조와 상태 UI 개편에 맞춰 v0.7.0으로 버전 갱신 (`dfd7b4a`)

## [v0.6.31](https://github.com/supremiere/DH-releases/releases/tag/v0.6.31) — 2026-10-01

### 추가

- add six-preset boss opening combo recorder (`13a35c5`)
- 콤보 재생 전후 어시스트 모드 토글 (`1b524ea`)
- manage portable combos in a top-level preset folder (`ae7e05d`)
- gate boss combos on ultimate readiness and simplify party startup (`f5a0a13`)
- 궁극기 재충전 콤보 반복 및 AI Connect 클리어 중단 (`ae453d4`)

### 테스트

- 어시스트 모드 H 토글 검증 (`3627c8b`)
- H 복귀 검증을 실제 바인딩 경로에 맞춤 (`d05aef6`)
- 자리비움 H 복귀 동작 반영 (`5d1e23b`)
- integrate combo cancellation with updated cutscene gate (`5bee6cd`)

### 문서

- 콤보 재생 전후 H 어시스트 토글 명시 (`7fbb19e`)
- H 복귀 입력 포커스 예외 설명 (`187d4f7`)
- 자리비움 운용 기준으로 H 복귀 설명 수정 (`cbacd14`)
- 보스전 오프닝 콤보 명칭 반영 (`97f07ed`)

### 수정

- 게임 창 비활성 시 H 복귀 입력 방지 (`8809068`)
- 자리비움 운용에서 어시스트 모드 복귀 보장 (`4c32880`)
- theme preset popup and add Space before automatic H combo (`543c4c9`)
- wait two seconds then Space before boss approach time (`c3e59d2`)
- use one-second skip delay and auto-enable cutscene skip (`f296cf3`)
- rename ultimate option to 궁극기 사용 (`0415e1c`)

### 기타

- 보스룸 스킬 명칭을 보스전 오프닝 콤보로 변경 (`7432c58`)
- 보스전 오프닝 콤보 설정 제목 통일 (`77ba77a`)
- bump release version to 0.6.31 (`cad1c79`)

### 빌드·배포

- PR 테스트 빌드 아티팩트 업로드 (`f809aeb`)

## [v0.6.30](https://github.com/supremiere/DH-releases/releases/tag/v0.6.30) — 2026-10-01

### 추가

- Android StoneMiner 1차 포팅 (`41c3c44`)

### 기타

- 모바일 포팅 코드를 DHmobile로 이동 (`eb2f454`)

### 수정

- v0.6.30 어비스 컷씬 확인 후 완료 탐색 및 60초 제한 제거 (`a06a15d`)

## [v0.6.29](https://github.com/supremiere/DH-releases/releases/tag/v0.6.29) — 2026-09-29

### 추가

- 어비스 보스 컷씬 감지 및 선택적 스킵 추가 (`182cc8c`)
- 어비스 부활 클릭 2초 후 스페이스 입력 추가 (`c818ec2`)
- 보스룸 스킬 순차 입력과 실시간 설정 반영 및 컷씬 오인식 방지 (`4289ff3`)

### 수정

- 여행자 간식 클릭 후 탐색 대기를 10분으로 변경 (`b188ed3`)
- 보스룸 스킬 기본 대기시간과 입력 순서 변경 (`ea2b609`)

### 기타

- v0.6.29 배포 버전 갱신 (`55b3360`)

## [v0.6.28](https://github.com/supremiere/DH-releases/releases/tag/v0.6.28) — 2026-09-27

### 수정

- 여행자 간식 클릭 완료 후 15분 재실행 대기 적용 (`d381c6f`)

## [v0.6.27](https://github.com/supremiere/DH-releases/releases/tag/v0.6.27) — 2026-09-27

### 수정

- 간식 인식 후 클릭 지연 해소 및 게임 창 중앙으로 커서 이동 (`19e55d0`)

### 기타

- v0.6.27 배포 준비 및 릴리즈 커밋 메시지 한글화 (`74d5453`)

## [v0.6.26](https://github.com/supremiere/DH-releases/releases/tag/v0.6.26) — 2026-09-27

### 수정

- 여행자 간식 10초 간격 처리 및 핵심 동작 우선 보장 (`26851c0`)

### 기타

- v0.6.26 배포 버전 갱신 (`d2f9267`)

## [v0.6.25](https://github.com/supremiere/DH-releases/releases/tag/v0.6.25) — 2026-09-26

### 수정

- 파티장 우연한 만남 자동 스왑 제거 (`2b7ebaf`)
- AI 커넥트 파티장 입장 확인/복구 루프 결합 (`b576b18`)

### 기타

- v0.6.25 배포 버전 갱신 (`f4439c2`)

## [v0.6.24](https://github.com/supremiere/DH-releases/releases/tag/v0.6.24) — 2026-09-26

### 수정

- confirm abyss leader entry using AI Connector region (`2380230`)

### 빌드·배포

- create release archive directory on clean checkout (`6b5a371`)

### 테스트

- verify entry confirmation for all three abyss regions (`123e512`)

## [v0.6.23](https://github.com/supremiere/DH-releases/releases/tag/v0.6.23) — 2026-09-26

### 기타

- 파티장 입장 실패 시 메뉴부터 재시작 (`d5b655c`)
- v0.6.23 버전 갱신 (`198fa17`)

## [v0.6.22](https://github.com/supremiere/DH-releases/releases/tag/v0.6.22) — 2026-09-25

### 기타

- 실제 자동 업데이트 테스트용 v0.6.22 배포 (`5dbb9fb`)

## [v0.6.21](https://github.com/supremiere/DH-releases/releases/tag/v0.6.21) — 2026-09-25

### 수정

- 업데이트 재실행 확인과 복구 보강 및 단계별 진행률 표시 (`a871f90`)
- 설치된 앱 재실행 시 추가 권한 창 없이 직접 프로세스 생성 (`ac3dce8`)

### 테스트

- 실제 패키지 교체 및 메인 창 준비 확인 검증 (`18679f8`)

## [v0.6.20](https://github.com/supremiere/DH-releases/releases/tag/v0.6.20) — 2026-09-25

- 배포 저장소에 버전별 변경 이력(`CHANGELOG.md`)을 추가했습니다.
- README에 최신 다운로드, 변경 이력, 설치 및 자동 업데이트 안내를 추가했습니다.
- README의 개발 소스 관련 문구를 삭제했습니다.
- v0.6.19에서 새 버전 감지 및 자동 업데이트를 테스트할 수 있도록 앱 버전을 v0.6.20으로 올렸습니다. 앱 기능은 v0.6.19와 동일합니다.

## [v0.6.19](https://github.com/supremiere/DH-releases/releases/tag/v0.6.19) — 2026-09-25

- 사이드바 버전 영역을 다른 버튼과 같은 모양의 `현재 버전 v…` 버튼 하나로 정리했습니다.
- 라이트·다크 테마를 지원하는 공통 팝업을 만들고 버전 확인에 적용했습니다.
- 최신 버전은 안내와 닫기 버튼을, 구버전은 최신 버전 번호·다운로드·닫기 버튼을 표시합니다.
- 다운로드 SHA-256 및 ZIP 경로·구조 검증을 추가했습니다.
- 설치 교체 후 시작 검사를 거쳐 재실행하고, 성공 시 구버전 파일과 임시 다운로드를 정리합니다.
- 교체 또는 시작 검사 실패 시 이전 버전으로 복구하도록 개선했습니다.

## [v0.6.18](https://github.com/supremiere/DH-releases/releases/tag/v0.6.18) — 2026-09-25

- 현재 버전과 최신 여부를 표시하고 수동 버전 확인 버튼을 추가했습니다.
- 최신 버전·새 버전 사용 가능·확인 실패 상태를 구분했습니다.
- 버전 확인을 백그라운드에서 실행하도록 개선했습니다.

## [v0.6.17](https://github.com/supremiere/DH-releases/releases/tag/v0.6.17) — 2026-09-25

- 이 저장소에 Windows 실행 패키지 ZIP을 처음 배포했습니다.
- 패키지 앱 시작 시 최신 GitHub Release를 확인하는 기능을 추가했습니다.
- 사용자 동의 후 새 버전을 다운로드하고 설치 폴더 교체 및 재실행을 진행하는 기능을 추가했습니다.
