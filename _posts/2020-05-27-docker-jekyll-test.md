---
title: 'docker로 jekyll 개발 환경 만들기'
date: 2020-05-27 00:12:49 +0900
tags: [docker, jekyll]
comments: true
---

### 1. docker로 jekyll 띄우기

```sh
export JEKYLL_VERSION=3.8 \
docker run -d --rm --name jekyll \
--volume="$PWD:/srv/jekyll" \
-p 4000:4000 -it jekyll/jekyll:$JEKYLL_VERSION \
/bin/bash
```

### 2. docker container 진입 후 다음 명령어를 차례대로 실행

```sh
bundle config set --local path vendor/bundle
bundle install
JEKYLL_ENV=production bundle exec jekyll serve -H 0.0.0.0
```

### 3. 4000번 포트로 접속하면 jekyll 화면을 볼 수 있습니다.

### 4. 참고한 정보

[jekyll-docker](https://github.com/envygeeks/jekyll-docker 'jekyll-docker'){:target="\_blank"}

[jekyll 로컬 서버 구동 방법](https://github.com/jekyllrb-ko/jekyllrb-ko.github.io 'Jekyll 문서 사이트 한글 번역'){:target="\_blank"}
