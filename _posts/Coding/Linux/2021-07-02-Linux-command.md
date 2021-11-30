---
title: Linux(debian) Command - 명령어에 대한 쉬운 해석...
date: 2021-07-02
categories: [Coding, Linux]
tags: [linux]
pin:
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>라즈베리파이를 구매하고 나서 처음으로 리눅스를 사용해봤다.  <br>국민(??)학교 시절 8비트 컴퓨터를 처음 접하면서 DOS 명령어중 dir/w가 기억나는 정도...<br>초심자로서 처음 사용하면서 궁금했던 내용들을 쓰려한다.

`Wiki's`
>

## Linux 기본 명령어
태어나서 처음으로 사용해본 리눅스 명령어들...

### 기본 상식
```
~/  #/home 폴더와 같음
../ #상위폴더
./  #현재폴더
*   #대상폴더의 모든 내용
```

### 파일, 폴더 복사 (cp) - copy
```
$ cp test.txt test1.txt
```

### 파일, 폴더 이동 (mv) - move
```
$ mv test.txt test_end.txt
```

```
$ mv old_folder new_folder
```

```
$ mv test.txt /home/test_end.txt
```

#### Advanced copy
파일 복사와 이동을 progress bar로 나타내준다.

#### pv
```
$ sudo apt install pv
```

```
$ pv 대상파일 > 복사위치
```

### 파일, 폴더 삭제 (rm) - remove
```
$ rm test.txt
```
