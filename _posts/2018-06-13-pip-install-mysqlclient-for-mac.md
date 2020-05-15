---
layout: post
title: "macOS에서 pip3 install mysqlclient 에러 대처법"
date: 2018-06-13 19:12:52 +0900
tags: [python, pip, mysql]
comments: true
---
### 1. Python에서 mysqlclient 설치시 발생하는 오류와 해결방안  

#### (1) mysqlclient

Python에서 MySQL DB접속을 하기 위해 필요한 모듈이며 pip3 install mysqlclient를 통해 설치를 해야 사용이 가능하다.  

#### (2) macOS에서 mysqlclient 설치

일반적으로 다음의 명령어를 통해서 설치를 할 수 있다.

```sh
pip3 install mysqlclient
```


#### (3) 오류발생

macOS의 경우 다음과 같은 오류가 발생한다.(테스트 환경 : macOS 10.13.5)

```sh
ld: library not found for -lssl
clang: error: linker command failed with exit code 1 (use -v to see invocation)
error: command '/usr/bin/clang' failed with exit status 1  
```


#### (4) 해결책

에러내용을 보면 ssl 모듈을 찾지 못해서 발생한다.  
그래서 다음과 같은 명령어로 ssl 모듈 경로를 지정해 주면 오류를 해결할 수 있다.

```sh
LDFLAGS=-L/usr/local/opt/openssl/lib pip3 install mysqlclient
```
