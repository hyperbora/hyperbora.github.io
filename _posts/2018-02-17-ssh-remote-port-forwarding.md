---
title: "SSH Port Forwarding (2)"
date: 2018-02-17 17:22:31 +0900
tags: [OS, ssh, forwarding]
comments: true
---

### 1. SSH를 이용한 포트포워딩 (Remote Port Forwarding)

#### (1) SSH Remote Port Forwarding

Local Port Forwarding과는 상황이 다르다. Remote Port Forwarding은 SSH 접속을 할 때 SSH 서버에 포트를 오픈하고 클라이언트에서 특정 포트를 지정하면 SSH로 생성한 터널을 통해 두개의 포트를 연결한다. 그리고 SSH 서버에서 오픈한 포트로 접속하면 클라이언트에서 오픈한 포트로 접속이 가능하다.

#### (2) 사용법

다음 명령어는 Remote Port Forwarding을 사용하는 하나의 예제이다.

``` sh
ssh -R *:13389:localhost:3389 ssh_user_id@ssh_server_ip
```

예제의 경우 SSH 기본포트(22)접속을 하면서 클라이언트는 3389를 오픈하고 서버에는 13389를 오픈한다.
그리고 서버에서 13389 포트를 통해서 최종적으로 방화벽에 막혀있는 클라이언트의 3389 포트로 접근이 가능하다. 터널을 통해서 연결하기 때문에 클라이언트 PC가 사설 아이피를 부여받고 있어도 접근이 가능하다.
