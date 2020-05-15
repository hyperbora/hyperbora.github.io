---
layout: posts
title: "Javascript에서 날짜 형식 지정해서 출력"
date: 2019-08-12 15:49:36 +0900
tags: [javascript]
comments: true
---
### 1. Javascript에서 날짜 형식 지정해서 출력하기

#### (1) 라이브러리 없이 자바스크립트로만 작성

```js
var d = new Date();
var date = [d.getFullYear(),
            ('0' + (d.getMonth() + 1)).slice(-2),
            ('0' + d.getDate()).slice(-2)].join('-');
var time = [('0' + d.getHours()).slice(-2), 
            ('0' + d.getMinutes()).slice(-2),
            ('0' + d.getSeconds()).slice(-2)].join(':');
console.log(`${date} ${time}`);
/* 2019-08-12 15:46:39 */
```
