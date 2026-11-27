# 작업사진 등록 (웹앱)

지점 작업사진을 폰·PC에서 등록하고, 작업 일정·캘린더·전체 내역으로 확인해 워드로 출력하는 웹앱입니다.
이 저장소에는 **화면(정적 파일)만** 들어 있습니다.

- 탭: **📅 일정 및 사진등록**(작업 일정 + 작업사진) · **📝 매장 요청** · **📋 전체 내역 조회**

- 저장된 사진과 기록은 Google Drive / Google Sheets 에 있고, 이 저장소에는 없습니다.
- 앱은 아래 Google Apps Script API 와 통신합니다(공개 실행 주소).
  `https://script.google.com/macros/s/AKfycbzK8wDACvACdG-Pvbanuuf3Gt2Egw4qxqCz-yTq_mkQHzdBHKX68sQiFKG-O_DGUwbi/exec`
  - 조회 `GET ?action=list|calendarbundle|calendar|workschedules|storerequests|export|exportrequests|drivestatus|uploadtoken`
  - 사진 빠른 업로드 `POST` `action=startDriveLink|pollDriveLink|getUploadToken|attachPhotoIds` (사진은 폰에서 구글 드라이브로 직접)
  - 저장 `POST` (JSON body, `Content-Type: text/plain`)
- 이 주소로 열면 Apps Script 화면이 아니라 이 정적 페이지가 뜨므로
  "이 애플리케이션은 Google Apps Script 사용자가 만들었습니다" 경고 띠가 나오지 않습니다.

## 파일

| 파일 | 용도 |
|---|---|
| `index.html` | 앱 화면 전체 (일정·사진 등록 / 달력 / 내역 조회 / 워드 출력) |
| `manifest.webmanifest` | 홈 화면에 추가했을 때 앱처럼 보이게 하는 설정 |
| `icon.svg`, `icon-192.png`, `icon-512.png` | 앱 아이콘 |

## 휴대폰 홈 화면에 추가

- **Android(Chrome)**: 주소창 오른쪽 ⋮ → **홈 화면에 추가**
- **iPhone(Safari)**: 공유 버튼 → **홈 화면에 추가**

## 배포

GitHub Pages 는 **`gh-pages` 브랜치 루트**에서 게시됩니다(같은 내용이 `main` 에도 들어 있습니다).
파일을 고친 뒤 두 브랜치에 함께 올리면 1~2분 안에
<https://ipcmaker-art.github.io/work-photo/> 에 반영됩니다.

```
git add -A && git commit -m "..."
git push origin main main:gh-pages
```
