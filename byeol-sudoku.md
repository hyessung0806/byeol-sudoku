---
type: project
aliases:
  - 별 사냥 스도쿠
  - 별 스도쿠
description: "Single-file PWA sudoku game for a 1st-grade child (star series), deployed on GitHub Pages. Reference for status: deployed and working; remaining is on-device landscape layout fine-tuning on Galaxy Tab."
author:
  - "[[김혜성]]"
date created: 2026-06-24
date modified: 2026-06-24
tags:
  - project
  - 별시리즈
  - PWA
status: 진행중
started: 2026-06-17
updated: 2026-06-24
remarks: "자동 업데이트(네트워크우선 sw, 재설치 없이 갱신) 완료. 남음: 실기기 가로 레이아웃 미세조정"
deploy: "https://hyessung0806.github.io/byeol-sudoku/"
stack: "단일 파일 PWA (HTML/CSS/JS, 무 CDN)"
---

# byeol-sudoku

## 개요
초등 1학년 딸용 단계별 스도쿠 PWA. **별 시리즈**의 첫 앱으로, 외부 라이브러리 없이 단일 `index.html`로 동작(오프라인). 점수·도장·연속 보상 구조 + 부모 모드.

## 산출물
- `index.html`(앱 전체) · `manifest.json` · `sw.js`(캐시 v7, 네트워크 우선) · 아이콘 3종 — 모두 저장소 루트
- GitHub Pages 자동 배포(`hyessung0806/byeol-sudoku`, `main`)

## 최근 작업
- 최신 핸드오프: [작업_핸드오프_2026-06-24.md](Hand-off/작업_핸드오프_2026-06-24.md)
- 결론(06-24): `sw.js`를 **네트워크 우선**으로 바꿔 코드 수정→push 시 **재설치 없이 자동 업데이트**(byeol-sugarugi와 동일). 캐시 v6→v7.
- 이전(06-18): 갤럭시탭 가로 정렬·세로모드 허용(`orientation: any`)·세로 중앙 배치.

## 남은 작업
- 실제 태블릿에서 가로 간격(`gap`) 미세조정 — 좁/넓다 싶으면 24~48px 사이
- 세로 고정 해제 확정 / 자동 업데이트 실기기 확인
