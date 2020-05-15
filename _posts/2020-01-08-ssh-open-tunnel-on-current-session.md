---
layout: post
title: "열려있는 SSH 세션에서 터널 생성하기"
date: 2020-01-08 20:11:05 +0900
tags: [ssh]
comments: true
---
### 1. 열려있는 SSH 세션에서 터널 생성하기

#### 터널생성을 위해 새로운 세션을 열어도 가능하지만 현재 세션에서도 생성이 가능합니다.


```sh
Supported escape sequences:
 ~.   - terminate connection (and any multiplexed sessions)
 ~B   - send a BREAK to the remote system
 ~C   - open a command line
 ~R   - request rekey
 ~V/v - decrease/increase verbosity (LogLevel)
 ~^Z  - suspend ssh
 ~#   - list forwarded connections
 ~&   - background ssh (when waiting for connections to terminate)
 ~?   - this message
 ~~   - send the escape character by typing it twice
(Note that escapes are only recognized immediately after newline.)
```


1. 엔터를 입력해서 터미널 입력 버퍼를 초기화 합니다.
1. **~?** 를 입력해서 사용가능한 명령어를 확인합니다._**(Supported escape sequences)**_
1. 엔터 입력 후 **~C** 를 입력해서 ssh prompt 로 진입합니다.
1. **ssh>** 가 앞에 붙습니다.
1. 터널 생성을 위한 커맨드를 입력합니다.
1. 예시는 로컬 포트포워딩이며 클라이언트 1111 포트와 ssh 서버 2222 포트를 연결합니다.
1. **ssh> -L 1111:localhost:2222**
1. 터널이 정상적으로 생성된다면 '**Forwarding port.**' 과 같은 메시지가 출력됩니다.
