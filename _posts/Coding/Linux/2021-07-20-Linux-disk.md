---
title: Linux(debian) - Disk 정보 확인 명령어 (lsblk, blkid, fdisk)
date: 2021-07-20
categories: [Coding, Linux]
tags: [linux]
pin:
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>리눅스에서는 물리적인 저장소를 Disk라 표시하고 Disk내의 구분은 Block으로 표시하는 듯하다. 윈도우의 Disk, Partition과 비슷한듯... 쓰는 용어 명령어들이 조금씩 다르다... 적응중...

`Wiki's`
>[전산](https://ko.wikipedia.org/wiki/전산) 분야에서(정확히 말해, 데이터 전송과 [기억 장치](https://ko.wikipedia.org/wiki/기억_장치)에서) **블록**(block)은 기억 공간을 나누는 단위이다.

## Disk, Block 관련 명령어

### df (Disk Free)
디스크 여유 공간 확인 명령어 주로 -h 와 함께 사용하면 용량단위를 보기 쉽게 표시해줌

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.6G     0  1.6G   0% /dev
tmpfs           340M   39M  301M  12% /run
overlay         1.7G  787M  912M  47% /
tmpfs           1.7G     0  1.7G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/mmcblk0p1  253M   63M  190M  25% /boot
/dev/sda1       117G   90G   22G  81% /home/DeukUSB
tmpfs           340M  4.0K  340M   1% /run/user/1001
```

### du (Disk Usage)

지정 폴더의 저장용량을 확인 가능하다.

```
$ du -sh /home
102G	/home
```

- -s : 요약정보(하위 폴더 제외)
- -h : 저장용량을 보기 쉽게 표시

### lsblk (List Block)

시스템에 있는 모든 저장소를 보여준다. disk는 물리적인 저장소, part는 해당 파티션을 보여줌


```
$ sudo lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda           8:0    1 119.2G  0 disk
└─sda1        8:1    1 119.2G  0 part /media/DeukTest/DeukUSB
mmcblk0     179:0    0 476.9G  0 disk
├─mmcblk0p1 179:1    0   256M  0 part /boot
└─mmcblk0p2 179:2    0 476.7G  0 part /
```

### blkid (Block ID)

리눅스는 일반적으로 UUID(저장소 고유번호), PARTUUID(파티션 고유번호), LABEL(포멧후 저장이름), /dev/(디바이스기준)으로 저장소를 지정 및 인식이 가능하다. <br>그러한 정보를 한번에 보여준다.

```
$ sudo blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="04A5-3FE5" TYPE="vfat" PARTUUID="71364f66-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="c1578b06-85c2-4327-9c65-4c474a8f23f9" TYPE="ext4" PARTUUID="71364f66-02"
/dev/mmcblk0: PTUUID="71364f66" PTTYPE="dos"
/dev/sda1: LABEL="DeukUSB" UUID="3941989C2008AD55" TYPE="ntfs" PARTUUID="bbb5899b-01"
```

### fdisk

fdisk --help 하면 -l은 list를 나타냄.

> -l, --list  display partitions and exit
아래와 같은 디스크 정보가 전부다 표시된다.

```
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


-------------

### [< Back to LINUX INDEX >](/categories/linux/)
