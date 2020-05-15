---
title: "macOS에서 쉘 명렁어로 알림을 띄우는 방법"
date: 2018-09-06 22:52:06 +0900
tags: [macOS, noti, osascript]
fullview: false
comments: true
---

### 1. macOS상에서 쉘 명령어로 알림을 띄우는 방법

#### 터미널에서 다음과 같은 명령어를 실행하면 오른쪽 상단에 소리와 함께 알림창이 나온다

``` sh
/usr/bin/osascript -e 'display notification "BODY" with title "TITLE" sound name ""'
```

여기서 BODY자리에는 본문을 TITLE 자리에는 제목을 입력한다
