# DungeonHelper releases

이 저장소는 DungeonHelper의 Windows 실행 파일 배포용입니다.

[최신 버전 다운로드](https://github.com/supremiere/DH-releases/releases/latest) · [버전별 변경사항](CHANGELOG.md)

## 설치 및 실행

1. 최신 릴리스의 `DungeonHelper-v<버전>-windows.zip`을 다운로드하세요.
2. ZIP 전체를 압축 해제하세요.
3. `DungeonHelper` 폴더 안의 `DungeonHelper.exe`를 실행하세요. `_internal` 폴더도 함께 있어야 합니다.

## 버전 확인과 업데이트

앱의 `현재 버전 v…` 버튼을 누르면 이 저장소의 최신 GitHub Release를 확인합니다.

- 최신 버전이면 `최신 버전입니다`와 `닫기` 버튼이 표시됩니다.
- 구버전이면 최신 버전 번호와 `최신 버전 다운 받기`, `닫기` 버튼이 표시됩니다.
- 다운로드 버튼을 누르면 파일 검증 후 앱을 종료하고 최신 버전으로 교체·재실행합니다. 시작 검사 성공 후 구버전 파일을 정리하며, 실패하면 이전 버전으로 복구합니다. 사용자 설정은 유지됩니다.

버전 비교는 README 문구나 저장소 커밋이 아닌 **최신 Release의 버전 태그**를 기준으로 합니다.

## 변경 이력 작성

앞으로 배포 스크립트를 실행하면 개발 저장소에서 이전 배포 이후의 커밋 메시지를 모아 `CHANGELOG.md`와 릴리스 설명을 자동으로 작성합니다. `feat:`, `fix:`, `docs:` 등의 커밋 접두어에 따라 변경사항을 분류합니다. 기존 버전의 변경 이력은 유지됩니다.
