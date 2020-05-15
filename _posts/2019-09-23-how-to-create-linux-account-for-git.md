---
layout: post
title: "git push, fetch 전용 리눅스 계정 만들기"
date: 2019-09-23 21:22:05 +0900
tags: [git]
comments: true
---
### 1. git push, fetch 전용 리눅스 계정 만들기

#### (1) 왜 전용 계정을 만들어야 하는가?

이 글은 github 등의 git 호스팅 서비스 대신에 자체 서버에

git을 구축해서 사용하는 경우에 해당하며 ssh 프로토콜을 통해

push, fetch를 사용할 때 적용할 수 있는 팁입니다.

ssh로 서버에 접근할 수 있는 계정으로 push, fetch를 해도 사용이 가능하지만

해당 계정으로 서버에 ssh접근이 가능하기 때문에 보안상 좋지 않습니다.

#### (2) git 전용계정 만들기

##### useradd로 git 계정을 만듭니다.
```sh
useradd 계정명
```
##### 계정확인
```sh
grep "git" /etc/passwd
git:x:1000:1000:git,git,,:/home/git:/bin/bash
```
##### /bin/bash 대신에 git 전용 shell로 변경
```sh
/etc/shells 에 git-shell이 설치된 경로를 마지막에 적어줍니다.

git 계정의 기본 쉘을 변경 합니다.
sudo chsh git -s $(which git-shell)
```
##### 접속을 위한 개인키 등록을 합니다.
```sh
vi ~/.ssh/authorized_keys 에 공개키를 등록하고 제일 앞에 다음 옵션을 추가합니다.

no-port-forwarding,no-X11-forwarding,no-agent-forwarding,no-pty

ssh 포트포워딩을 방지하는 옵션입니다!
```
##### 제한된 쉘 접근을 위해 커멘트를 추가합니다.
```sh
sudo cp -r /usr/share/doc/git/contrib/git-shell-commands /home/git/
sudo chmod 750 /home/git/git-shell-commands/*
sudo chown -R git:git /home/git/
```