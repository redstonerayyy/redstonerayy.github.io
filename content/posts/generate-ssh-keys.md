---
title: How to generate SSH Keys
releasedate: "6.10.23"
lastchanged: "6.10.23"
type: post
summary: "A simple listing of commands on how to generate SSH Keys with OpenSSL."
---

Use [ssh-keygen](https://man.openbsd.org/ssh-keygen) by OpenSSH.

ed25519 for elliptic curve algorithm (better) and rsa for
prime factorization algorithm

```shell
ssh-keygen -t ed25519 -C "<label>"
ssh-keygen -t rsa -b 4096 -C "<label>"
```
