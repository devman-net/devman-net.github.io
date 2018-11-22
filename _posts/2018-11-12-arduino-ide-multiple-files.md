---
layout: post
title:  아두이노(Arduino) IDE 다중 파일 코딩하기
categories: Arduino
tags: arduino-ide, multiple-files
---

* content
{:toc}

## 아두이노(Arduino) IDE 다중 파일

요즘 새로운 장난감 Arduino를 가지고 놀고 있는데 흥미로운 사항이 있어서 글을 남긴다.  

![](https://i.imgur.com/ihk7JvY.png "Arduino IDE 새 탭")

>Arduino IDE에서 `새 탭`을 이용, 소스 파일을 `분할`하여 코딩할 수 있다. 말 그대로 소스 파일들이
>분할만 되는 것이다. 그리고 컴파일 시의 병합은 알파벳 순(오름차순)으로 된다.
>
>따라서 함수 선언부와 구현을 잘 조합한다면, 의미있는 함수들의 집합을 만들어 소스를 관리할 수 있을 것이다.
>다만 알파벳 순이라는 제약사항을 잘 핸들링 해야할 것이다.
>
>`전역 변수(Global Variable)`의 경우 알파벳 순으로 볼 때 `후순위 분할 파일`에 있는 전역 변수를
>`선순위 분할 파일`에서 호출할 수 없다. 이런 경우, 컴파일 시에 에러가 발생한다.


### 다중 파일 예
files: multiple.ino, sub.ino

``` c++
// file: multiple.ino

int _mainGlobalVariable;

void MainFunction() {
	Serial.println("main function");
}

void setup() {
  SubFunction();            // sub.ino 파일에 있는 함수 호출
  _subGlobalVariable = 0;   // sub.ino 파일에 있는 전역변수 접근
}

void loop() {
  // put your main code here, to run repeatedly:
}
```

``` c++
// file: sub.ino

int _subGlobalVariable;

void SubFunction() {
  MainFunction();           // multiple.ino에 있는 함수 호출
  _mainGlobalVariable = 0;  // multiple.ino에 있는 전역변수 접근
}
```

### 컴파일 결과 (Error 발생)
``` bash
c:\projects\multiple\multiple.ino: In function 'void setup()':

multiple:22:3: error: '_subGlobalVariable' was not declared in this scope

   _subGlobalVariable = 0; // sub.ino 파일에 있는 전역변수 접근

   ^

exit status 1
'_subGlobalVariable' was not declared in this scope
```

>`multiple.ino`{:.language-csharp .highlight}에서 `sub.ino`{:.language-csharp .highlight}에 있는
>`_subGlobalVariable = 0;`{:.language-csharp .highlight}에 접근할 수 없다. (컴파일 오류 발생)
>기능은 재미가 있으나 실제로 사용하기는 쉽지 않을 듯 싶다. *(선언부를 위한 파일을 사용하면 될 듯...)*  
>


### 테스트 환경
> Arduino IDE 1.8.7
