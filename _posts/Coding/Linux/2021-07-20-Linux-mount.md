---
title: Linux(debian) - Disk Mount(자동) 명령어 (mount, unmount, fstab)
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

```bash
/dev/sda1 is mounted; will not make a filesystem here!
```
>Mount되어 있으면 포맷이 안된다.

```bash
$ sudo umount /dev/sda1
```
>해당 SD 카드를 unmount한다.


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
## Mount 하기

```bash
mount [option] [device] [directory]
```
option
- -a :/etc/fstab 에 있는 모든 시스템을 마운트
- -t : 파일 시스템을 지정 (ex:-t ext4)
- -o : 다른 옵션 지정

 ```bash
 $ sudo mount -t ntfs -o uid=DeukTest,gid=DeukTest /dev/sda1 /home/DeukTest
 ```
 >ntfs Filesystem에 한해서만 소유자 지정이 가능하다. <br>


### 폴더 소유자 변경
```bash
$ sudo chown -R deuktest:deuktest /home/DeukTest
```
### 폴더 권한 변경
```bash
$ sudo chmod -R 755 /home/DeukTest
```

## Unmout 하기

```bash
$ umount /dev/sda1
```
>

## 재부팅시 자동 Mount하기
라즈베리파이(리눅스)는 USB 삽입하고 GUI Desktop에서 쉽게 마운트 가능하다. 하지만 위치가 내가 원하는 곳(/media/pi/)이 아니고 재부팅시에는 자동으로 인식이 되지않는다.
>자동으로 ROOT에 /media 에 마운트된다.

```bash
$ sudo lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda           8:0    1 119.2G  0 disk
└─sda1        8:1    1 119.2G  0 part /media/flyingdeuk/DeukCloud
mmcblk0     179:0    0 476.9G  0 disk
├─mmcblk0p1 179:1    0   256M  0 part /boot
└─mmcblk0p2 179:2    0 476.7G  0 part /
```

```bash
$ sudo blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="04A5-3FE5" TYPE="vfat" PARTUUID="71364f66-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="c1578b06-85c2-4327-9c65-4c474a8f23f9" TYPE="ext4" PARTUUID="71364f66-02"
/dev/mmcblk0: PTUUID="71364f66" PTTYPE="dos"
/dev/sda1: LABEL="DeukCloud" UUID="3941989C2008AD55" TYPE="ntfs" PARTUUID="bbb5899b-01"
```

ntfs-3g : 더이상 필요하지 않음

현재 mount되어 있는 저장소의 정보를 확인한다.


fdisk --help 하면 -l은 list를 나타냄.

> -l, --list  display partitions and exit
아래와 같은 디스크 정보가 전부다 표시된다.

```bash
$ sudo fdisk -l
.
.
.
Disk /dev/mmcblk0: 476.9 GiB, 512074186752 bytes, 1000144896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x71364f66

Device         Boot  Start        End   Sectors   Size Id Type
/dev/mmcblk0p1        8192     532479    524288   256M  c W95 FAT32 (LBA)
/dev/mmcblk0p2      532480 1000144895 999612416 476.7G 83 Linux


Disk /dev/sda: 119.2 GiB, 128035323904 bytes, 250068992 sectors
Disk model: USB Flash Drive
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbbb5899b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *       64 250068991 250068928 119.2G  7 HPFS/NTFS/exFAT
```

```bash
proc            /proc           proc    defaults          0       0
PARTUUID=71364f66-01  /boot           vfat    defaults          0       2
PARTUUID=71364f66-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
```

```bash
drwxr-xr-x  8 root       root       4096  7월 14 07:20 .
drwxr-xr-x 19 root       root       4096  7월 14 18:46 ..
drwxrwxrwx  1 root       root       4096  7월  1 17:18 DeukCloud
drwxrwxr-x  5 flyingdeuk flyingdeuk 4096 12월 20  2020 DeukCloud1
drwxr-xr-x 20 flyingdeuk flyingdeuk 4096  7월 14 17:47 flyingdeuk
drwxr-xr-x  2 iel        iel        4096 12월 20  2020 iel
drwxr-xr-x  2 ina        ina        4096 12월 20  2020 ina
drwxr-xr-x  2 sunny      sunny      4096 12월 20  2020 sunny
```

```bash
proc            /proc           proc    defaults          0       0
PARTUUID=71364f66-01  /boot           vfat    defaults          0       2
PARTUUID=71364f66-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=3941989C2008AD55 /home/DeukCloud ntfs uid=1001,gid=1001,umask=002 0 0
# LEXAR auto mount
```
> noatime 옵션은 access time에 대해 기록을 하지 않아 약간 성능 향상을 볼 수 있습니다

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

/etc/fstab 파일이 잘못된 채로 Linux 부팅을 시도하면 중간에 실패 메시지와 함께 부팅이 되지 않는다.
이 때 콘솔에서(네트워크 사용 불가) repair or recovery 모드로 로그인이 가능한데,
여기서 fstab을 수정한 뒤 reboot 해주면 된다.

1) 아래와 같은 메시지가 나오면 root password 를 이용하여 recovery 모드 로그인
Give root password for maintenance
(or type Control-D to continue):
Ctrl+D 를 눌렀을 경우는 그대로 부팅을 진행하라는 뜻인데 현재 상태가 정상이 아니므로 fail 된다.

2) 현재 read-only mode 이므로 /etc/fstab 파일을 수정할 수 없다. 루트 파일시스템을 다시 mount 하여 read-write mode로 변경한다.
# mount -o remount,rw /
3) /etc/fstab 파일을 수정한다.
4) reboot
