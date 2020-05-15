---
layout: post
title: "Windows용 git bash에서 SSH 개인키를 이용한 접속이 안되는 경우 해결책"
date: 2018-11-30 15:22:36 +0900
tags: [OS, ssh, openssh]
comments: true
---
### 1. Windows용 git bash에서 SSH 개인키를 이용한 접속이 안되는 경우 해결책

#### (1) 현상 확인
다음 명령어로 디버깅을 해서 원인을 파악한다. 여기서 git 자리에 본인의 아이디를 입력하는 것이 아니라 git 그대로 입력한다.
```sh
ssh -Tv git@github.com
```
디버깅 로그를 통해 전반적은 문제를 확인해서 개인키를 찾는 경로가 올바르게 설정되어 있는지 확인한다.

#### (2) 개인키 확인
개인키 생성을 puttygen을 통해서 생성했다면 git bash는 puttygen에서 생성한 개인키 형식을 해석할 수 없어서 에러가 발생한다.
[참고](https://stackoverflow.com/questions/41563973/git-clone-key-load-public-invalid-format-permission-denied-publickey/41564430)


해당 링크에서 확인했듯이 puttygen에서 기존 개인키를 불러와서 OpenSSH Key로 변환한다.


기본의 개인키에 OpenSSH Key로 변환한 키로 덮어쓴다.

#### (3) 테스트
(1)의 명령을 다시 실행하면 다음과 같은 성공 메시지를 확인할 수 있다.(Username 자리에 본인의 아이디가 표시된다.)
```sh
Hi Username! You've successfully authenticated, but GitHub does not provide shell access.
```