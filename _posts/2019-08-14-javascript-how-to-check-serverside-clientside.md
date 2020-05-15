---
layout: post
title: "Javascript에서 서버 사이드, 클라이언트 사이드 구분하는 방법"
date: 2019-08-14 11:12:21 +0900
tags: [javascript]
comments: true
---
### 1. Javascript에서 서버 사이드, 클라이언트 사이드 구분하는 방법

#### (1) if 조건문으로 서버에서 실행되는지 클라이언트에서 실행되는지 구분하는 코드

```js
if (typeof window === "undefined") {
    // nodejs
} else {
    // browser
}
```
