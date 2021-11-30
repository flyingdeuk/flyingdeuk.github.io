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

## mount - Mount 하기

```bash
mount [option] [device] [directory]
```
**option**
- -a :/etc/fstab 에 있는 모든 시스템을 마운트
- -t : 파일 시스템을 지정 (ex:-t ext4)
- -o : 다른 옵션 지정

```bash
$ sudo mount /dev/sda1 /home/DeukTest
```
> 일반적인 경우 위와 같이 간단하게 mount가능하다.

#### 특정 사용자로 Mount하기 (NTFS)
리눅스에서 사용하는 ext4와 같은 포멧은 소유자와 권한등의 변경이 자유롭다. 하지만 NTFS의 경우는 mount시 지정하지 않으면 나중에 변경이 불가능하고 전체를 똑같이 지정할 수 밖에는 없다.

```bash
$ id
uid=1001(DeukTest) gid=1001(DeukTest) groups=1001(DeukTest),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),44(video),46(plugdev),60(games),100(users),105(input),109(netdev),126(debian-transmission),997(gpio),998(i2c),999(spi)
```
>id 명령어로 현재 사용자의 id를 알수 있다. 해당 id로 mount하는 법은 아래와 같다. (단, ntfs에만 적용 가능하다...) -> 다른 file system의 경우엔 chown으로 가능하겠다.

 ```bash
 $ sudo mount -t ntfs -o uid=DeukTest,gid=DeukTest,umask=002 /dev/sda1 /home/DeukTest
 ```
 >ntfs Filesystem에서는 최초 마운트시에 소유자 및 소유그룹지정 및 권한 설정이 가능하다. 이후에는 불가능하고 전체 디스크에 동일하게 적용이 된다.
 <br>


## umount - Umount 하기

```bash
$ umount /dev/sda1
```
>unmount는 단순하다. 해당 device를 그냥 unmount... 메모리 안전하게 제거와 비슷한 느낌??


## fstab - 재부팅시 자동 Mount
Mount는 GUI에서 일반적으로 이동식 Disk와 유사한 개념으로 삽입/제거의 목적으로 하드웨어를 연결한다. <br>
fstab은 하드웨어를 시스템의 일부로 연결하는 방법인듯 하다.

### 정보 확인하기

```bash
$ sudo lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda           8:0    1 119.2G  0 disk
└─sda1        8:1    1 119.2G  0 part /media/DeukTest/DeukUSB
mmcblk0     179:0    0 476.9G  0 disk
├─mmcblk0p1 179:1    0   256M  0 part /boot
└─mmcblk0p2 179:2    0 476.7G  0 part /
```
> lsblk (list block)으로 Disk(Block)의 이름을 알 수 있다.

```bash
$ sudo blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="04A5-3FE5" TYPE="vfat" PARTUUID="71364f66-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="c1578b06-85c2-4327-9c65-4c474a8f23f9" TYPE="ext4" PARTUUID="71364f66-02"
/dev/mmcblk0: PTUUID="71364f66" PTTYPE="dos"
/dev/sda1: LABEL="DeukUSB" UUID="3941989C2008AD55" TYPE="ntfs" PARTUUID="bbb5899b-01"
```
> blkid(blick id)로 해당 저장소의 아이디를 알 수 있다. <br>
리눅스에서는 기본적으로 UUID, PARTUUID, Divice name(sda1), LABEL의 모든 id로 인식이 가능하다. <br>

장단점이야 Device는 USB port 1, 2에 의해 결정되고, UUID, PARTUUID, LABEL등은 어디에 꽂든지 해당 저장소를 인식한다는 차이...

### fstab 수정

```bash
$ sudo cat /etc/fstab

proc            /proc           proc    defaults          0       0
PARTUUID=71364f66-01  /boot           vfat    defaults          0       2
PARTUUID=71364f66-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
```
> 기본적인 fstab file 내용 <br>
SD 저장소에 boot section과 저장을 위한 partition이 나누어져 있는 것을 볼 수 있다.

#### 일반적인 경우

```bash
$ sudo vim /etc/fstab

proc            /proc           proc    defaults          0       0
PARTUUID=71364f66-01  /boot           vfat    defaults          0       2
PARTUUID=71364f66-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=3941989C2008AD55 /home/DeukUSB ext4 defaults 0 0
# USB auto mount
```
> 특별한 option없이 이렇게만 해도 일반적으로 사용하는 데는 문제가 없다.


#### 일부 option 적용 예(NTFS)
ntfs의 경우 mount시 소유자와 권한을 지정하지 않으면 않되므로 fstab에서도 지정을 해야지만 소유자, 권한을 설정할 수 있다.

```bash
$ sudo vim /etc/fstab

proc            /proc           proc    defaults          0       0
PARTUUID=71364f66-01  /boot           vfat    defaults          0       2
PARTUUID=71364f66-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=3941989C2008AD55 /home/DeukUSB ntfs uid=1001,gid=1001,umask=002 0 0
# USB auto mount
```
> vi, nano, vim등의 편집기를 이용해서 위와 같이 추가해준다. <br>

**uid=1001,gid=1001,umask=002 0 0**

- **uid=1001,gid=1001**
> 위에서 **id**의 사용자 정보로 mount가능하다. <br>**ntfs**에 한해 위와 같이 사용자 및 사용자 그룹을 지정해서 자동 mount가 가능하다.(이유는 못 찾겠다.)

- **umask=002**
> 여기 저기 많이 찾아 봤지만 umask의 설명이 어렵다. <br>
chmod의 보수라고 생각하면 쉽다. <br>**umask=002**는 결국 해당 폴더에 **chmod -R 775**와 같은 권한 설정이라 생각하면 된다. (mount하면서 폴더 권한을 지정할 수 있다.)<br>

- **noatime**
> access time에 대해 기록을 하지 않아 약간 성능 향상을 볼 수 있다고 한다.

- **0**      **0**
> 첫번째 **0**은 덤프(백업) 가능은 **1** 불가능은 **0** <br>
두번째 **0**은 무결정 검사 유무 **0**은 불요, **1 or 2**는 우선순위이다.

#### 오류의 탄생
fstab은 시스템을 결정해서 인지 매우 민감하다.

**/dev/sda1** -> **dev/sda1** : 먹통

**defaults** -> **default** : 먹통

**ntfs** -> **Nfts** : 먹통
>왼쪽이 맞는 표현, 오른쪽은 오류를 탄생시킨다.

#### 오류의 해결
fstab의 오류가 탄생되면 부팅이 안된다.

**Give root password for maintenance
(or type Control-D to continue):**
> 위 메세지와 함께 멈춘다면 root 암호를 입력해 recovery mode에서 fstab을 수정한다.


**$ vim /etc/fstab**
> 혹여나 권한의 문제로 안 될 경우는 `mount -o remount,rw /` 로 rw로 다시 마운트 하면 된다고 함...

**reboot**

-------

### PostScript
개인적으로 리눅스의 초보자로써 CLI를 기준으로 뭔가를 setup하는 거에 흥미를 느낀다.

윈도우나 맥같은 GUI의 상황에서는 마우스 오른쪽 클릭과 함께 어디에 디스크를 지정할지... 정하고 권한도 별로 신경쓰지않으니까...

위와 같은 방법으로 마운트하면 내 시스템내의 하나의 폴더에 내 저장소를 마치 하나의 시스템처럼 mount할 수 있다는 점이 매력으로 다가온다.
