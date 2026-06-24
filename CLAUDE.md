# 별 사냥 스도쿠 — Claude Code 작업 규칙

초등 1학년 아이용 단계별 스도쿠 PWA. GitHub Pages로 배포되는 **단일 파일 정적 사이트**.
- 배포 주소: https://hyessung0806.github.io/byeol-sudoku/
- 원격 저장소: hyessung0806/byeol-sudoku (브랜치 `main`)

## 파일 구조 (모두 저장소 루트에 위치)
- `index.html` — 앱 전체 (HTML + CSS + JS 한 파일). 거의 모든 작업은 여기서.
- `manifest.json` — PWA 정보 (이름, 아이콘, landscape 고정)
- `sw.js` — 오프라인 캐싱 서비스워커
- `icon-192.png` / `icon-512.png` / `icon-maskable-512.png` — 앱 아이콘
- `README.md` — 설치 안내 / `HANDOFF.md` — 프로젝트 맥락

## 작업이 끝나면 항상 (필수)
1. `git add . && git commit -m "<요약>" && git push` — **push까지 해야** 사이트에 반영됨.
2. **자동 업데이트(v7~):** `sw.js`가 HTML을 **네트워크 우선**으로 받으므로 `index.html` 내용을 고쳐 push하면 태블릿에서 **앱을 (온라인으로) 다시 열 때 자동 반영**된다. 캐시 버전(`byeolsudoku-vN`)은 더 이상 매번 올릴 필요 없고, **`sw.js` 자체나 `ASSETS` 프리캐시 목록을 바꿀 때만** 올린다.
3. 모든 파일은 **루트에 유지**. 하위 폴더로 옮기면 Pages 주소가 깨짐.

## 설정 상수 (index.html `<script>` 위쪽)
- `LEVEL_TARGET=50` : 한 난이도 통과 문제 수
- `DAILY_TARGET=2`  : 하루 미션 문제 수
- `POINTS=20000`    : 한 문제 점수
- `STAGES[]` : 단계 추가는 한 줄. 예) `{ size:16, label:"16×16", boxRows:4, boxCols:4 }`
  (조건: `boxRows × boxCols === size`)

## 지켜야 할 원칙
- 저장은 localStorage지만 **항상 `Store` 래퍼(try/catch + 메모리 폴백)** 를 거친다. 직접 localStorage 호출 금지.
- 아이용 앱 → 문구는 쉽고 격려하는 톤. 점수·도장·연속 등 보상 구조는 유지.
- 힌트는 정답을 채우지 말고 "가장 쉬운 칸"을 짚어 **푸는 길만** 안내 (현재 로직 유지).
- **외부 라이브러리·CDN 없이 단일 파일** 유지 (오프라인 동작 보장).
- 진행 기록(점수·도장)은 코드가 아니라 기기 데이터 → 재배포해도 지워지지 않음. 안심하고 배포.

## 테스트
빌드 없음. 로컬 확인: 폴더에서 `python3 -m http.server 8000` → http://localhost:8000
(서비스워커·PWA 설치는 localhost 또는 https에서만 동작)
