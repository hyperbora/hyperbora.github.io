---
layout: posts
title: "winscp를 이용한 특정 폴더 동기화"
date: 2020-01-06 14:01:01 +0900
tags: [winscp]
comments: true
---
### 1. winscp를 이용한 특정 폴더 동기화

#### (1) winscp로 scp를 통해 파일을 동기화 하는 예시입니다.

* WinSCP_path : winscp가 설치된 경로
* log_path : log 가 저장될 경로
* private_key_path : 개인키 경로
* ssh_fingerprint : ssh fingerprint
* client_path : 동기화가 될 윈도우PC 경로
* server_path : 파일을 가져올 서버 경로
* filemask : 특정 파일을 포함하거나, 제외할 경우 추가

```sh
@echo off

"WinSCP_path" ^
  /log="log_path" /logsize=1*5M /loglevel=0 /ini=nul ^
  /privatekey="private_key_path" ^
  /command ^
    "open sftp://id@host:port -hostkey=""ssh_fingerprint""" ^
    "synchronize local client_path server_path -mirror -filemask=""[0-9]+.aac;*.m4a|*AppleDouble/""" ^
    "exit"

set WINSCP_RESULT=%ERRORLEVEL%
if %WINSCP_RESULT% equ 0 (
  echo Success
) else (
  echo Error
)

exit /b %WINSCP_RESULT%
```
