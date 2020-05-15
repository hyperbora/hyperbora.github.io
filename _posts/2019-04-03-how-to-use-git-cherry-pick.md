---
layout: posts
title: "git cherry-pick 사용법"
date: 2019-04-03 19:49:35 +0900
tags: [git]
comments: true
---
### 1. GIT cherry-pick 사용방법

#### (1) cherry-pick?

다른 브런치에 있는 커밋을 현재 브런치에 적용하고 싶은 경우가 있다.
즉 merge나 rebase 하는 대신에 특정 커밋만 가져오고 싶을 때 사용한다.

#### (2) 사용방법

```sh
git cherry-pick <commit-id>
```


#### (3) 충돌이 나는 경우

당연히 충돌이 발생할 수 있으며 충돌이 난 경우 충돌 해결 후 다음 명령어를 실행한다.

```sh
git cherry-pick --continue
```
