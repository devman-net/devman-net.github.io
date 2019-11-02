---
layout: post
title:  Linux Deploy - Ubuntu 설치
categories: Etc
tags: linux-deploy busy-box ubuntu
---

* content
{:toc}
## Linux Deploy - Ubuntu 설치하기
### 2018.12.05 현재 버전  
> Samsung Galaxy S3 (SHV-E210S)  
> Android 4.4.4 (KitKat)  
> Linux Deploy 2.2.1-243  
> BusyBox 1.29.3-meefik  

인터넷 상에 Ver 2.x에서 Linux 설치가 되지 않는다는 글들이 있는데 [Linux Deploy Wiki][github-linux-deploy-wiki]의 정보를 잘 읽으면 정상적인 설치가 될 것 같다. 물론 단말기와 환경에 따라서 실패할 가능성이 없지는 않다.  

### 설치 순서
1 단말기를 Rooting한다.  
2 Google Play에서 `Linux Deploy`{:style="color:white"}를 검색하여 단말기에 설치한다.  
3 BusyBox 설치 - Linux Deploy 화면의 링크`이 경로`{:style="color:red"}를 통하여 BusyBox 프로그램을 단말기에 설치한다.  

![](https://i.imgur.com/Gf5JzMD.png "Linux Deploy '이 경로' 링크 클릭")

4 BusyBox 실행 `설치`{:style="color:white"} 버튼 클릭하여 BusyBox를 설치한다.  

![](https://i.imgur.com/xxE1Br5.png "BusyBox 설치된 화면")
![](https://i.imgur.com/xHo62rX.png "BusyBox 정보")  

5 `Linux Deploy`{:style="color:white"} 설정을 변경한다. PATH 경로: `/system/xbin`{:style="color:white"}로 변경, `ENV 업데이이트`{:style="color:red"} 클릭  

![](https://i.imgur.com/wumHc7N.png "Linux Deploy 메뉴 > 설정")
![](https://i.imgur.com/FXKZb9T.png "Linux Deploy 설정 > PATH 경로, ENV 업데이트")

6 Linux Deploy에서 설치할 리눅스를 선택하고 몇 가지 설정을 변경한다.  
>배포: Ubuntu  
>이미지 크기(MB): 2000 [문제해결 링크][github-linux-deploy-solve] (필자는 2048로 설정한 경우 실패했다.)  
>지역화, SSH, GUI 활성화

![](https://i.imgur.com/SOoKK8S.png "Linux Deploy 속성 > 운영체제, 이미지 크기")
![](https://i.imgur.com/YXLlN5X.png "Linux Deploy 속성 > 파일 시스템, 지역화")
![](https://i.imgur.com/Chdzlq1.png "Linux Deploy 속성 > SSH, GUI 활성화")

7 Ubuntu 설치, (메인화면 우측상단 클릭 > 컨텍스트 메뉴 > 설치)  

![](https://i.imgur.com/7564q1c.png "Linux Deploy > Ubuntu 설치 확인")
![](https://i.imgur.com/qFDs1SO.png "Linux Deploy > SU 루트권한 요청 > 허용")

8 정상적으로 설치가 된다면 시간이 흐른뒤에 `<<< deploy`{:style="color:red"}가 출력되면 모든 설치가 끝난 것이다.  

![](https://i.imgur.com/kY1u72J.png "Linux Deploy > Ubuntu 설치 완료")

## 서비스 시작 (16.04 실패)
설치가 잘 됐으니 이제 하단의 `시작`{:style="color:white"}를 클릭하여 Ubuntu를 시작한다.  

``` console
[20:08:03] >>> start
[20:08:04] Checking file system ... skip
[20:08:04] Mounting the container:
[20:08:04] / ... skip
[20:08:04] /proc ... skip
[20:08:04] /sys ... skip
[20:08:04] /dev ... skip
[20:08:04] /dev/shm ... skip
[20:08:04] /dev/pts ... skip
[20:08:04] :: Configuring core/mnt ...
[20:08:04] :: Configuring core/net ...
[20:08:04] :: Starting desktop/dbus ... fail
[20:08:04] :: Starting extra/ssh ... fail
[20:08:04] :: Starting graphics/vnc ... fail
[20:08:04] <<< start
```

dbux, ssh, vnc를 시작하지 못했다.  
자세한 정보를 보기 위해서 `우측상단 > 컨텍스트 메뉴 > 상태`{:style="color:white"}를 클릭한다.

``` console
[20:11:10] >>> status
[20:11:10] Device: SHV-E210S
[20:11:10] Android: 4.4.4
[20:11:10] Architecture: armv7l
[20:11:10] Kernel: 3.0.31-9579646
[20:11:10] Memory: 50/1786 MB
[20:11:10] Swap: 991/1023 MB
[20:11:10] SELinux: active
[20:11:10] Loop devices: yes
[20:11:10] Support binfmt_misc: yes
[20:11:10] Supported FS: exfat ext2 ext3 ext4 fuseblk msdos vfat
[20:11:10] Installed system: Ubuntu 16.04 LTS
[20:11:10] Status of components:
[20:11:11] :: desktop/dbus ... stopped
[20:11:11] :: extra/ssh ... stopped
[20:11:11] :: graphics/vnc ... stopped
[20:11:11] Mounted parts:
[20:11:11] * /
[20:11:11] * /proc
[20:11:11] * /sys
[20:11:11] * /dev
[20:11:11] * /dev/shm
[20:11:11] * /dev/pts
[20:11:11] Available mount points:
[20:11:11] * /sys/kernel/debug  0.0/0.0 GB (debugfs)
[20:11:11] * /system  0.1/2.0 GB (ext4)
[20:11:11] * /efs  0.0/0.0 GB (ext4)
[20:11:11] * /cache  1.0/1.0 GB (ext4)
[20:11:11] * /preload  0.4/0.6 GB (ext4)
[20:11:11] * /data  10.0/10.8 GB (ext4)
[20:11:11] * /mnt/shell/knox-emulated  10.0/10.8 GB (sdcardfs)
[20:11:11] * /mnt/shell/emulated  10.0/10.8 GB (sdcardfs)
[20:11:11] * /storage/emulated/0  10.0/10.8 GB (sdcardfs)
[20:11:11] * /storage/emulated/0/Android/obb  10.0/10.8 GB (sdcardfs)
[20:11:11] * /storage/emulated/legacy  10.0/10.8 GB (sdcardfs)
[20:11:11] * /storage/emulated/legacy/Android/obb  10.0/10.8 GB (sdcardfs)
[20:11:11] Available partitions:
[20:11:11]  ...no available partitions
[20:11:11] <<< status
```

문제점에 대한 검색 결과 Kernel의 버전이 문제가 되는 것으로 보인다.  
현재 `Ubuntu 16.04 LTS(Xenial)`{: style="color:white"}를 설치했는데,
다시 `Ubuntu 14.04 LTS(Trusty)`{: style="color:white"}를 설치해본다.

## Ubuntu 14.04 LTS(Trusty) 설치
서비스 시작 로그
``` console
20:54:09] >>> start
[20:54:09] Checking file system ... skip
[20:54:09] Mounting the container:
[20:54:09] / ... skip
[20:54:09] /proc ... skip
[20:54:09] /sys ... skip
[20:54:09] /dev ... skip
[20:54:09] /dev/shm ... skip
[20:54:09] /dev/pts ... skip
[20:54:10] :: Configuring core/mnt ...
[20:54:10] :: Configuring core/net ...
[20:54:10] :: Starting desktop/dbus ... done
[20:54:10] :: Starting extra/ssh ... skip
[20:54:11] :: Starting graphics/vnc ... done
[20:54:11] <<< start
```

ssh가 skip이다. 자세한 정보를 확인한다.
`우측상단 > 컨텍스트 메뉴 > 상태`{:style="color:white"}를 클릭한다.

``` console
[20:55:18] >>> status
[20:55:19] Device: SHV-E210S
[20:55:19] Android: 4.4.4
[20:55:19] Architecture: armv7l
[20:55:19] Kernel: 3.0.31-9579646
[20:55:19] Memory: 88/1786 MB
[20:55:19] Swap: 923/1023 MB
[20:55:19] SELinux: active
[20:55:19] Loop devices: yes
[20:55:19] Support binfmt_misc: yes
[20:55:19] Supported FS: exfat ext2 ext3 ext4 fuseblk msdos vfat
[20:55:19] Installed system: Ubuntu 14.04 LTS
[20:55:19] Status of components:
[20:55:19] :: desktop/dbus ... started
[20:55:19] :: extra/ssh ... started
[20:55:19] :: graphics/vnc ... stopped
[20:55:19] Mounted parts:
[20:55:19] * /
[20:55:19] * /proc
[20:55:19] * /sys
[20:55:19] * /dev
[20:55:19] * /dev/shm
[20:55:19] * /dev/pts
[20:55:19] Available mount points:
[20:55:19] * /sys/kernel/debug  0.0/0.0 GB (debugfs)
[20:55:19] * /system  0.1/2.0 GB (ext4)
[20:55:19] * /efs  0.0/0.0 GB (ext4)
[20:55:19] * /cache  1.0/1.0 GB (ext4)
[20:55:19] * /preload  0.4/0.6 GB (ext4)
[20:55:19] * /data  9.5/10.8 GB (ext4)
[20:55:19] * /mnt/shell/knox-emulated  9.5/10.8 GB (sdcardfs)
[20:55:19] * /mnt/shell/emulated  9.5/10.8 GB (sdcardfs)
[20:55:19] * /storage/emulated/0  9.5/10.8 GB (sdcardfs)
[20:55:19] * /storage/emulated/0/Android/obb  9.5/10.8 GB (sdcardfs)
[20:55:19] * /storage/emulated/legacy  9.5/10.8 GB (sdcardfs)
[20:55:19] * /storage/emulated/legacy/Android/obb  9.5/10.8 GB (sdcardfs)
[20:55:19] Available partitions:
[20:55:20]  ...no available partitions
[20:55:20] <<< status
```
ssh가 정상적으로 시작되었음이 확인됐다.

### SSH(Secure Shell) 연결
[Xshell][xshell-download]을 이용하여 연결했다. (물론 다른 프로그램을 사용해도 ...)

```console
Connecting to 192.168.0.7:22...
Connection established.
To escape to local shell, press 'Ctrl+Alt+]'.

Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.0.31-9579646 armv7l)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Ubuntu 14.04 LTS [running via Linux Deploy]
devman@localhost:~$
```

#### 연결은 됐으나...
{:.no_toc}

``` console
devman@localhost:~$ sudo apt-get update
sudo: PERM_ROOT: setresuid(0, -1, -1): Permission denied
devman@localhost:~$
```
Permission denied 오류가 발생한다.  
관련 Issue : https://github.com/meefik/linuxdeploy/issues/224  


### Permission denied 우회

우회 방법 > `root`{:style="color:white"} 계정으로 로그인 하기
1. root 계정의 비밀번호 설정  
2. root 계정으로 ssh 로그인 할 수 있도록 `sshd_config` 수정  
3. 서비스 재시작  

`Linux Deploy`로 설치한 Ubuntu에 접근하기 위해서 `ADB(Android Debug Bridge)`를 사용한다.

1. 단말기의 `USB 디버깅 모드`{:style="color:white"} 활성화  
2. ADB (Android Debug Bridge) 설치

ADB Shell 실행 > su

``` console
$ adb shell
shell@c1skt:/ $ su
root@c1skt:/ #
```

`sh /data/data/ru.meefik.linuxdeploy/files/bin/linuxdeploy shell`{:.language-cpp .highlight}
에서 `/files/bin/` 이 경로는 다를 수 있다.  

``` console
root@c1skt:/ # sh /data/data/ru.meefik.linuxdeploy/files/bin/linuxdeploy shell
Checking file system ... done
Mounting the container:
/ ... done
/proc ... done
/sys ... done
/dev ... done
/dev/shm ... done
/dev/pts ... done
/proc/sys/fs/binfmt_misc ... done
:: Configuring core/mnt ...
:: Configuring core/net ...
Ubuntu 14.04 LTS [running via Linux Deploy]
root@localhost:/#
```

*root*{:style="color:white"} 계정의 비밀번호를 변경한다.

``` bash
root@localhost:/# passwd root
passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@localhost:/#

```

*sshd_config*{:style="color:white"}를 확인한다.

``` bash
root@localhost:/# cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin yes
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
```

확인 결과 이미 `PermitRootLogin yes`{:style="color:yellow"}로 설정되어 있다.  
Version에 따라서 다른 것으로 보이므로 상황에 맞게 대응하면 된다.  
sshd_config를 수정하지 않았으므로 서비스를 재시작하지 않는다. 재시작을 하려면 `service sshd restart`  

#### root 계정으로 로그인이 가능한가?  
{:.no_toc}
```console
ssh root@192.168.0.7
root@192.168.0.7's password:
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.0.31-9579646 armv7l)

 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Ubuntu 14.04 LTS [running via Linux Deploy]
root@localhost:~#
```
정상적으로 로그인이 되며 간단한 `apt-get update`도 성공했다.  
사용자 계정에 root 권한을 주면 된다는 얘기도 있으나, 아직까지 성공하지 못했다.

## ADB Error

### error: device not found >
{:.no_toc}
USB 디버깅 모드가 활성화 되었는지 확인한다.

### error: device offline >
{:.no_toc}
adb kill-server  
adb start-server  
adb devices

``` bash
$ adb kill-server

$ adb start-server
* daemon not running. starting it now on port 5037 *
* daemon started successfully *

$ adb devices
List of devices attached
42f7d71116f7bf29	device
```
그래도 문제가 해결이 안 된다면, 단말기를 재부팅한다.

## 참조 사이트
>[GitHub - Linux Deploy] [github-linux-deploy]  
>[GitHub - Linux Deploy Wiki] [github-linux-deploy-wiki]  

## Download Link
>[XShell] [xshell-download]  
>[ADB Shell] [adb-shell]  
>*Linux Deploy 2.x* 에서 설치가 되지 않는 경우...  
>[Linux Deploy 1.5.6] [linux-deploy-1-5-6]  
>[BusyBox 1.24.1] [busybox-1-24-1]  


{::comment}
**이 사이트 내 링크**  
>[Linux Deploy 1.5.6] [linux-deploy-1-5-6-devman]  
>[BusyBox 1.24.1] [busybox-1-24-1-devman]  
>[ADB Shell] [adb-shell-devman]  

{:/comment}

[github-linux-deploy]: https://github.com/meefik/linuxdeploy "Linux Deploy GitHub"
[github-linux-deploy-wiki]: https://github.com/meefik/linuxdeploy/wiki "Linux Deploy Wiki"
[github-linux-deploy-solve]: https://github.com/meefik/linuxdeploy/wiki/%EB%AC%B8%EC%A0%9C%EB%A5%BC-%ED%95%B4%EA%B2%B0%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95 "Linux Deploy 문제를 해결하는 방법"
[xshell-download]: https://www.netsarang.co.kr/download/down_form.html?code=612 "Xshell 6 Download - 개인 사용자 무료"

[linux-deploy-1-5-6]: https://linux-deploy.en.uptodown.com/android "Linux Deploy 1.5.6"
[busybox-1-24-1]: https://github.com/meefik/busybox/releases/download/1.24.1/busybox.apk "BusyBox 1.24.1"
[adb-shell]: http://adbshell.com/upload/adb.zip "ADB Shell"

{::comment}
[linux-deploy-1-5-6-devman]: ../assets/linux-deploy-ubuntu/linux-deploy-1-5-6.apk "Linux Deploy 1.5.6 (devman.net)"
[busybox-1-24-1-devman]: ../assets/linux-deploy-ubuntu/busybox.apk "BusyBox 1.24.1 (devman.net)"
[adb-shell-devman]: ../assets/linux-deploy-ubuntu/adb.zip "ADB Shell (devman.net)"

{:/comment}
