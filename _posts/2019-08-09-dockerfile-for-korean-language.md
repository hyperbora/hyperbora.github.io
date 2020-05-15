---
layout: post
title: "Ubuntu 도커 환경에서 한글이 제대로 안나올 때 해결방법"
date: 2019-08-09 21:45:51 +0900
tags: [docker]
comments: true
---
### 1. Ubuntu 도커 환경에서 한글이 제대로 안나올 때 해결방법

#### (1) 도커 파일에 해당 명령어 추가

```sh
RUN apt-get -y update && apt-get -y upgrade && apt-get -y install locales
RUN sed -i 's/^# \(ko_KR.UTF-8\)/\1/' /etc/locale.gen
RUN localedef -f UTF-8 -i ko_KR ko_KR.UTF-8
RUN echo 'export LC_ALL=ko_KR.UTF-8' >> ~/.bashrc
RUN echo 'export LANG=ko_KR.UTF-8' >> ~/.bashrc
RUN echo 'export LANGUAGE=ko_KR.UTF-8' >> ~/.bashrc
```

#### (2) 명령어 설명

##### apt-get으로 업데이트 후 locales 설치
##### /etc/locale.gen 에서 한글 관련 주석 해제
##### localedef로 한글 locale 설치
##### .bashrc 파일에 한글 관련 설정

#### (2) 도커파일 빌드

##### 해당 도커 파일로 빌드 후 실행하면 한글이 잘 나오는 것을 확인 할 수 있습니다.