---
title: "Windows 환경에서 node-sass 설치 관련해서 오류나는 경우 해결책"
date: 2019-06-12 17:46:00 +0900
tags: [npm]
comments: true
---

### 1. Windows 환경에서 node-sass 설치 관련해서 오류나는 경우 해결책

#### (1) 현상

윈도우 환경에서 react 관련 책의 예제를 실행하던 중 node-sass 관련해서 오류가 나는 상황 발생

#### (2) 해결책

기존에 설치된 node-sass를 제거하고 최신 node-sass를 설치 합니다.
환경에 따라 -g 옵션 등을 추가합니다.

``` sh
npm uninstall node-sass && npm install node-sass
```
