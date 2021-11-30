---
title: Linux(debian) - 소유권, 권한 변경 명령어 (chown, chmod, umask)
date: 2021-07-20
categories: [Coding, Linux]
tags: [linux]
pin:
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>

`Wiki's`
>

### 폴더 소유자 변경
```bash
$ sudo chown -R deuktest:deuktest /home/DeukTest
```
### 폴더 권한 변경
```bash
$ sudo chmod -R 755 /home/DeukTest
```
### 파일 생성 권한
```bash
Umask    Created Files       Created Directories
------------------------------------------------
000(0)   666 (rw-rw-rw-)     777     (rwxrwxrwx)
002(2)   664 (rw-rw-r--)     775     (rwxrwxr-x)
022(18)  644 (rw-r--r--)     755     (rwxr-xr-x)
027(23)  640 (rw-r-----)     750     (rwxr-x---)
077(63)  600 (rw-------)     700     (rwx------)
277(191) 400 (r--------)     500     (r-x------)
```
