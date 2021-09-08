---
title: Linux(debian) - Disk Format 명령어 (mkfs, mke2fs, mke2fs)
date: 2021-07-20
categories: [Coding, Linux]
tags: [linux]
pin:
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>

`Wiki's`
>**파일 시스템**(file system, [문화어](https://ko.wikipedia.org/wiki/문화어): 파일체계)은 컴퓨터에서 [파일](https://ko.wikipedia.org/wiki/파일)이나 [자료](https://ko.wikipedia.org/wiki/자료)를 쉽게 발견 및 접근할 수 있도록 보관 또는 조직하는 체제를 가리키는 말이다.




```bash
/dev/sda1 is mounted; will not make a filesystem here!
```
>Mount되어 있으면 포맷이 안된다.

```bash
$ sudo umount /dev/sda1
```
>해당 SD 카드를 unmount한다.


```bash
$ sudo mke2fs -t ext4 -L Deuk -v /dev/sda1
mke2fs 1.44.5 (15-Dec-2018)
/dev/sda1 contains a ext4 file system
	last mounted on Tue Jul 20 14:15:31 2021
Proceed anyway? (y,N) y
fs_types for mke2fs.conf resolution: 'ext4'
Filesystem label=Deuk
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7815168 inodes, 31258616 blocks
1562930 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2178940928
954 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Filesystem UUID: 6623e408-3e34-48a3-be7e-031cd21d0e42
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
	4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (131072 blocks): done
Writing superblocks and filesystem accounting information: done
```
```bash
$ sudo mkfs.fat -F 32 -n DeukTest -v /dev/sda1
```
> -F : FAT32/16 설정 <br>
-n : 레이블 명 <br>
-v : 자세한 수행 정보 출력

```bash
$ sudo mkntfs -f -L DeukTest -v /dev/sda1
```
> -f : fast 포멧  <br>
-L : 레이블 명 <br>
-v : 자세한 수행 정보 출력

```bash
$ sudo mke2fs -t ext4 -L DeukTest -v /dev/sda1
```
> -f : fast 포멧  <br>
-L : 레이블 명 <br>
-v : 자세한 수행 정보 출력

```bash
$ ls -al /usr/sbin
.
.
.
lrwxrwxrwx  1 root root         6  1월 10  2020 mkfs.ext2 -> mke2fs
lrwxrwxrwx  1 root root         6  1월 10  2020 mkfs.ext3 -> mke2fs
lrwxrwxrwx  1 root root         6  1월 10  2020 mkfs.ext4 -> mke2fs
-rwxr-xr-x  1 root root     34752  5월 13  2018 mkfs.fat
-rwxr-xr-x  1 root root     87520  1월 10  2019 mkfs.minix
lrwxrwxrwx  1 root root         8  5월 13  2018 mkfs.msdos -> mkfs.fat
lrwxrwxrwx  1 root root         6  3월 22  2019 mkfs.ntfs -> mkntfs
lrwxrwxrwx  1 root root         8  5월 13  2018 mkfs.vfat -> mkfs.fat
.
.
.
```

### 폴더 소유자 변경
```bash
$ sudo chown -R deuktest:deuktest /home/DeukTest
```
### 폴더 권한 변경
```bash
$ sudo chmod -R 755 /home/DeukTest
```
