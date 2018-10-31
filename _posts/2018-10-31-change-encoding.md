---
layout: post
title:  Encoding 변경하기
categories: Etc
tags: Visualstudio Encoding
---

* content
{:toc}

## Visual Studio에서 Encoding 변경하기

개발 작업을 할 때 여러 개의 Editor나 IDE를 사용하여 개발을 진행하는 데 가끔씩 Encoding이
의도와는 다르게 적용되는 경우들이 있다. (파일 탐색기에서 새 텍스트 문서를 만드는 경우 등)
Github에서 소스를 확인할 때 텍스트가 깨져서 나오는 경우 당혹스럽기까지 하다.

#### 실행 방법
{:.no_toc}

> - Encoding을 변경할 파일을 `Visual Studio`에서 열기
> - 파일 메뉴에서 `고급 저장 옵션` 클릭
> - `고급 저장 옵션` 다이얼로그 박스에서 `유니코드(서명 있는 UTF-8) - 코드 페이지 65001`로 변경

##### 파일 메뉴
{:.no_toc}

![img-file-menu]
{: width="500px" height="430px"}

##### 고급 저장 옵션
{:.no_toc}

![img-file-dialog]

##### 인코딩 종류 선택
{:.no_toc}

![img-file-select]

[img-file-menu]: https://i.imgur.com/rjRhrZB.png "Menu"
[img-file-dialog]: https://i.imgur.com/zJkp2aw1.png "Advanced Save Options"
[img-file-select]: https://i.imgur.com/jpvj4d1.png "Encoding"
