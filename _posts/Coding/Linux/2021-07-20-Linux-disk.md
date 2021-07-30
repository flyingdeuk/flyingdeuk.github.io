---
title: Linux(debian) - Disk 정보 확인 명령어 (lsblk, blkid, fdisk)
date: 2021-07-20
categories: [Coding, Linux]
tags: [linux]
pin:
typora-root-url: ../../../../flyingdeuk.github.io
---

![command](/img/coding/linux/command.jpg)

`FlyingDeuk's`
>

`Wiki's`
>


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
