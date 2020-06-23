---
title: 'ssh tunnel 전용 계정 만들기'
date: 2020-06-23 22:30:30 +0900
tags: [ssh]
comments: true
---

### 1. tunnel 전용 계정을 만드는 이유

일반계정으로 터널을 생성하게 되면 해당 계정으로 쉘 접근이 가능해서 터널 전용 계정을 만들어서 운영하는게 좋습니다.

### 2. tunnel 전용 계정 생성

```sh
# -s 옵션으로 쉘 접근이 불가한 쉘을 지정하는게 핵심입니다.
# 계정명(예시는 tunnel)은 변경 가능합니다.
useradd -s /bin/false tunnel
```

### 3. tunnel 계정에 ssh 공개키 등록

```sh
cd ~tunnel
mkdir .ssh
cd .ssh
touch authorized_keys
chmod 644 authorized_keys
vi authorized_keys
cd ~tunnel
chown -R tunnel:tunnel *
```

### 4. 원격머신에서 ssh 접속으로 터널 생성

```sh
# 핵심은 -N 옵션입니다. 해당 계정은 /bin/false로 인해 쉘 접근이 불가하지만
# -N 옵션으로 ssh 접속이 끊어지지 않게 유지해 줍니다.
ssh -p port -N -i /path/to/private -R *:1234:localhost:1234 tunnel@ssh_server
```
