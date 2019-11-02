---
layout: post
title:  Git Commands
categories: Etc
tags: git
---

* content
{:toc}

## Git Commands
자주 사용하지 않아서 머릿속에서 잊혀져가는 Git Command들을 정리한다.

#### Repository 관련

원격 Repository Url 확인

```bash
$ git config --get remote.origin.url
https://github.com/devman-net/devman-net.git
```

```bash
$ git remote -v
origin	https://github.com/devman-net/devman-net.git (fetch)
origin	https://github.com/devman-net/devman-net.git (push)
```

원격 Repository 추가
```bash
usage: git remote add [<options>] <name> <url>

$ git remote add repository-name git-url
```

Repository 이름 변경
```bash
usage: git remote rename <old> <new>

$ git remote rename old-name new-name
```

#### Source 파일 이름 변경 및 경로 이동
개발중에 namespace등의 변경으로 인해 파일의 이름이나 경로가 변경되는 경우가 있다.
이럴 때 IDE에서 무심코 이름을 변경했다가는 아주 피곤한 상태가 된다.
```bash
git mv [<options>] <source>... <destination>

$ git mv old-path/old-name.cs new-path/new-name.cs
```
