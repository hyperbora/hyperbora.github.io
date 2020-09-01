---
title: 'autossh를 이용한 ssh 터널 생성'
date: 2020-09-01 23:15:33 +0900
tags: [ssh]
comments: true
---

### 1. autossh 란?

이름에서 알 수 있듯이 ssh 연결이 끊어지면 자동으로 재연결을 해주는 프로그램입니다.

### 2. 활용방법

ssh로 터널을 생성해서 네트워크가 끊어지는 등의 문제가 발생하여도 autossh를 통해 자동으로 재연결을 해줍니다.

해당 프로그램은 유닉스 기반 프로그램이어서 Windows 기반에서는 사용할 수 없습니다.

하지만 Windows에서 Ubuntu를 최근에 설치가 가능해서 Ubuntu 설치 후 autossh를 실행하는 형식으로는 가능합니다.

### 3. 스크립트

해당 스크립트를 사용하시는 환경에 맞게 수정 후 vbs 파일로 저장합니다. 저장한 파일을 Windows 시작프로그램에 등록합니다. (실행 -> shell:startup)

```sh
# SSH_PORT : SSH 서버 접속 포트(기본 포트 22)
# REMOTE_PORT : SSH 서버에서 오픈할 포트
# LOCAL_PORT : SSH 클라이언트에서 오픈할 포트
# ID : SSH 접속 계정
# SSH_SERVER_IP : SSH 서버 IP
Set ws = CreateObject("Wscript.Shell")
ws.run "wsl -d ubuntu -u root autossh -f -M 13000 -N -i /root/.ssh/id_rsa -p SSH_PORT -o ""StrictHostKeyChecking=no"" -o ""ExitOnForwardFailure=yes"" -o ""ServerAliveInterval 30"" -o ""ServerAliveCountMax 3"" -R REMOTE_PORT:localhost:LOCAL_PORT ID@SSH_SERVER_IP", vbhide
```

### 4. 작동원리

Windows가 시작되면 시작프로그램에 등록된 스크립트를 실행하게 되며 Ubuntu 실행 후 내부에서 autossh를 구동하며 해당 창은 숨김 처리를 합니다.
