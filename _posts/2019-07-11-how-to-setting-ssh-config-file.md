---
layout: posts
title: "SSH 연결을 IP혹은 도메인 별로 설정하는 방법"
date: 2019-07-11 11:33:00 +0900
tags: [SSH]
comments: true
---
### 1. SSH 연결을 IP혹은 도메인 별로 설정하는 방법

#### (1) 사용하는 이유

아이디, 패스워드를 매번 입력해서 ssh 접속을 하는 경우는 문제가 없으나


개인키를 통한 접속을 하는 경우 유저명이나 개인키 경로를 따로 설정해야 하는 경우가 있습니다.


#### (2) 설정방법

사용자 홈디렉토리에 아래에 있는 .ssh 디렉토리로 가서 config 파일을 만들거나 수정합니다.

윈도우 경로 : C:\Users\계정명\\.ssh

리눅스, 맥 경로 : ~/.ssh

아래 예시는 github에 연결할 때를 가정한 설정입니다.

```sh
Host github.com
    HostName github.com
    User git
    IdentityFile <key_location>
```

#### (3) 추가 설명

Host 는 별칭을 의미하며 ssh 연결시에 config 파일에 해당 Host와 일치하는 정보가 있으면

HostName에 해당하는 서버에 접속을 시도합니다. HostName은 실제 서버의 도메인이거나

아이피 주소여야 합니다.

User는 기본 접속 계정 정보이며 IdentityFile 는 개인키 경로를 나타냅니다.