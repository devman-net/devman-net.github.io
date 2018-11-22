---
layout: post
title:  아두이노(Arduino) 클래스 만들기
categories: Arduino
tags: arduino-ide, create-class
---

* content
{:toc}

## 시작하기 앞서서
아두이노 클래스 만들기, 또는 사용하기를 검색하면 `라이브러리`라는 단어가 대부분을 차지한다.
모든 글들을 읽어 본 것은 아니지만, 읽어 본 글들은 실제로 `라이브러리`화 해서 사용하는 것에
대한 설명이 주를 이뤘다.  
그래서 처음에 아두이노에서 클래스(Class)는 라이브러리를 만드는 경우에만 사용하나? 생각도 했었다.  
결론은 클래스를 바로 적용할 수 있다는 것!

왜 그럴까?

## 클래스 및 헤더 파일 만들기 (Arduino IDE)

![](https://i.imgur.com/ihk7JvY.png "Arduino 새 탭")

화면에 표시된 컨텍스트(Context) 메뉴에서 `새 탭` 항목을 클릭한다.
![](https://i.imgur.com/O6LadqG.png "Arduino 컨텍스트 메뉴 - 새 탭")

`새로운 파일을 위한 이름` 텍스트 박스에 클래스의 이름과 확장자(소스: cpp, 헤더: h)를 입력하고 확인을 클릭한다.
![](https://i.imgur.com/4rxSywJ.png "Arduino 새로운 파일을 위한 이름:")

`NewClass.cpp 탭`{:.language-cpp .highlight}이 추가된 것을 확인할 수 있다.
![](https://i.imgur.com/jEbcgSs.png "Arduino NewClass.cpp 탭")

> `새로운 파일을 위한 이름`에 확장자를 입력하지 않을 경우 `ino`파일이 생성된다.

## 클래스 소스 확인
>Visual Studio VMicro에서 새 클래스를 생성한 경우이다.

`NewClass.h`
~~~cpp
// file: NewClass.h
#ifndef _NEWCLASS_h
#define _NEWCLASS_h

#if defined(ARDUINO) && ARDUINO >= 100
	#include "arduino.h"
#else
	#include "WProgram.h"
#endif

class NewClass
{
 public:
	void toString();
};

extern NewClass New;

#endif
~~~

`NewClass.cpp`
~~~cpp
// file: NewClass.cpp
#include "NewClass.h"

void NewClass::toString()
{
	Serial.println("NewClass::toString");
}

NewClass New;
~~~

`multiple.ino`
~~~cpp
// file: multiple.ino
#include "NewClass.h" // 새로 만든 클래스 header 추가

void setup() {
  Serial.begin(115200);
  NewClass _newcls;
  _newcls.toString();
}

void loop() {

}
~~~

## 마치며
작은 크기의 프로그램을 개발하는 경우라면 아두이노에서 클래스를 만들어 사용할 일은 없겠지만,
그렇다고 라이브러리로 사용한다는 식으로 알려주는 것은 아니라는 생각이 든다.  
>요즘 재미삼아 이것 저것 해보고 있는데 80C196을 사용했던 시절에 비해서 매우 편해졌다는 생각이 든다.  
>가격도 무척 저렴하고... 호환 보드는 더~ 저렴하고... 예전 기억도 새록새록 나고... 아~ 납땜의 추억!!!
