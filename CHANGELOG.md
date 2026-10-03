# 변경 이력

DungeonHelper Windows 배포 버전의 변경사항입니다. 최신 버전부터 정리합니다.

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
