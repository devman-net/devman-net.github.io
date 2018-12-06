---
layout: post
title:  VMWare Shared Folder 설정 [Ubuntu]
categories: Etc
tags: vmware shared-folder linux ubuntu
---

* content
{:toc}

## VMware 공유 폴더 설정하기
VMWare를 사용하면서 Host OS와 Guest OS간 폴더의 공유 필요성을 느낄 때가 있다.  
이럴 때 VMWare의 공유 폴더 기능을 사용하면 편하다.

### VMWare Shared Foler 추가
>Guest OS에 공유할 폴더를 추가한다.  

1 VMWare Menu > VM > `Settings...`{:.language-cpp .highlight} 클릭  

![](https://i.imgur.com/ysf4O66.png?1 "VMWare 설정 메뉴")

2 Options Tab > Shared Folders (Guest OS와 공유할 폴더를 추가하거나 제거한다.)  

![](https://i.imgur.com/FHe3eOp.png?1 "VMWare 설정 옵션")

### Reinstall VMWare Tools
>Host의 폴더를 Guest OS에 Mount하기 위해서 VMWare Tool을 재설치 한다.  

1 VMWare Menu > VM > `Reinstall VMWare Tools...`{:.language-cpp .highlight} 클릭  

![](https://i.imgur.com/1DsIRie.png?1 "VMWare Tools 재설치")

2 DVD 형태로 Mount된 것을 확인할 수 있다.

![](https://i.imgur.com/BgQBNrF.png "VMWare Tools 재설치")

3 `VMwareTools-10.1.15-6627299.tar.gz`{:.language-cpp .highlight} 파일을 적당한 폴더에 압축을 푼다.  

- Downloads 폴더에 압축을 푼다. `tar -xvvzf VMwareTools-10.1.15-6627299.tar.gz -C ~/Downloads/`{:.language-cpp .highlight}  
- 압축이 풀린 경로로 이동 `cd ~/Downloads/vmware-tools-distrib`{:.language-cpp .highlight}  

4 vmware-install.pl 명령을 실행하여 VMWare Tools를 설치한다. `./vmware-install.pl`{:.language-cpp .highlight}  

``` bash
user@ubuntu:/media/user/VMware Tools$ tar -xvvzf VMwareTools-10.1.15-6627299.tar.gz -C ~/Downloads/
user@ubuntu:/media/user/VMware Tools$ cd ~/Downloads/vmware-tools-distrib
user@ubuntu:~/Downloads/vmware-tools-distrib$ sudo ./vmware-install.pl
```

### 설치완료 확인
`/mnt/hgfs/`{:.language-cpp .highlight} 폴더 안에 공유 설정한 폴더가 보이는지 확인한다. 폴더가 확인되지 않는 경우 재부팅을 한다.
``` bash
user@ubuntu:~$ ls /mnt/hgfs/
share
```

### 테스트 환경
> VMWare Workstation 14 Pro  
> Host OS: Windows 10 x64  
> Guest OS: Ubuntu 16.04 LTS  
