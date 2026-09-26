# 변경 이력

DungeonHelper Windows 배포 버전의 변경사항입니다. 최신 버전부터 정리합니다.

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
