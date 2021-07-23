---
title: Linux(debian) Command - 명령어에 대한 쉬운 해석...
date: 2021-07-02
categories: [Coding, Linux]
tags: [linux]
pin:
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>

`Wiki's`
>

## Linux 기본 명령어
태어나서 처음으로 사용해본 리눅스 명령어들...

### 기본 상식
```bash
~/ #/home 폴더와 같음
../ #상위폴더
./ #현재폴더
* #대상폴더의 모든 내용

```

### 파일, 폴더 복사 (cp) - copy
```bash
$ cp test.txt test1.txt
```

### 파일, 폴더 이동 (mv) - move
```bash
$ mv test.txt test_end.txt
```

```bash
$ mv old_folder new_folder
```

```bash
$ mv test.txt /home/test_end.txt
```
#### Advanced copy
파일 복사와 이동을 progress bar로 나타내준다.

#### pv
```bash
$ sudo apt install pv
```

```bash
$ pv 대상파일 > 복사위치
```


### 파일, 폴더 삭제 (rm) - remove
