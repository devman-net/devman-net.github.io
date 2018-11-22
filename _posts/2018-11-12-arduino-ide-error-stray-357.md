---
layout: post
title:  아두이노(Arduino) IDE 컴파일 오류 - Stray 357, 273, 277
categories: Arduino
tags: arduino-ide, error-stray-357
---

* content
{:toc}

## 아두이노(Arduino) IDE 컴파일 오류

### 컴파일 오류 메시지
```bash
error: stray '\357' in program
error: stray '\273' in program
error: stray '\277' in program
```

### 소스 파일 인코딩 문제
Arduino IDE를 사용하여 소스 파일을 생성한다면 문제가 없을 듯 하지만, 외부 에디터를 사용하는 경우
인코딩이 달라 Arduino IDE에서 컴파일 시에 위의 오류가 발생할 수 있다.

|-------------+------------------+-------|
| Dev Tool    | Default Encoding | Error |
|-------------|:-----------------|:------|
| Arduino IDE       | Unicode(서명 없는 UTF-8) - 코드 페이지 65001 | |
| Visual Studio C++ | 한국어 - 코드 페이지 949 | Error |
| Visual Studio C++ | Unicode(서명 있는 UTF-8) - 코드 페이지 65001 | Error |

`한국어 - 코드 페이지 949`{:.language-bash .highlight}의 경우는 Arduino IDE가 친절하게 방법을 알려주지만
`Unicode(서명 있는 UTF-8) - 코드 페이지 65001`{:.language-bash .highlight}의 경우는 위의 오류를 출력한다.

### 해결방법
오류가 발생한 해당 소스 파일의 Encoding을 `Unicode(서명 없는 UTF-8) - 코드 페이지 65001`{:.language-bash .highlight} 변경하면 된다.

### 테스트 환경
> Arduino IDE 1.8.7
