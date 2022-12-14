---
title: '[42seoul] ft_containers'
date: '2023-01-05'
tags: ['5th_circle', 'C++', '42seoul', 'Containers']
draft: false
summary: The standard C++ containers have all a specific usage. To make sure you understand them, let’s re-implement them!
layout: PostSimple
---

# ft_containers

이번 과제는 워낙 방대한 양이라 조금씩 정리할 예정이다.

## Contents

- [Chapter 1]
- [Chapter 2]
- [Chapter 3]
- [Chapter 4]

## Chapter 1

### Objectives

이번 프로젝트에서, 너는 C++ 표준 템플릿 라이브러리의 몇가지 타입을 구현할 것이다.

각 표준 컨테이너의 구조를 참고해야한다. OCCF의 일부가 누락된 경우, 구현하지 않아야 한다.

다시 말하자면, C++98 표준을 준수해야 하므로, 컨테이너의 이후 기능들은 구현하면 안되지만, 모든 98버전의 기능들은 구현해야한다. (더 이상 사용하지 않는 기능도 포함된다.)

## Chapter 2

### General Rules

#### 컴파일

- 너의 C++ 코드는 "-Wall -Wextra -Werror" 플래그와 함께 컴파일 한다.
- 너의 코드는 "-std=c++98"를 플래그로 추가하고도 컴파일이 되어야 한다.
- 너의 소스 파일을 컴파일 하기 위한 **Makefile**을 제출해야한다. 리링크는 허용되지 않는다.
- 너의 Makefile은 다음 규칙이 포함되어야 한다: $(NAME), all, clean, fclean, and re.

##### 포멧과 네임 컨벤션

- 각각의 컨테이너는 적절한 이름의 클래스 파일을 제출해야 한다.

- **Goodbye Norminette!** 코딩 스타일을 강요하지 않는다. 너가 좋아하는 것을 따라 할 수 있다. 하지만 동료평가시, 이해할 수 없는 코드를 사용할 경우, 동료들이 점수를 줄 수 없다는 것을 명심해라. 최선을 다해 클린하고 가독성 있는 코드를 작성하길 바란다.

##### 허용되는 사항 / 금지되는 사항

너는 이제부터 C로 코딩하지 않는다. C++의 시간이다 ! 그러므로:

- 너는 표준 라이브러리에서의 거의 모든 것들을 사용할 수 있다. 따라서, 이미 알고 있는 것을 고수하는 대신, 익숙한 C함수의 C++ 버전을 최대한 많이 사용해보는 것이 현명할 것이다.

- 그러나, 너는 다른 외부 라이브러리를 사용할 수 없다. 이 말의 의미는 C++ 11과 Boost 라이브러리가 금지된다는 것이다. 다음 함수도 금지된다. printf(), alloc() and free(). 이걸 쓰면 너의 점수는 0점이 될 것이다.

##### 몇 가지 디자인 요구사항

- 메모리 누수가 발생하는것은 C++도 동일하다. 만약 너가 메모리를 할당하면, 메모리 누수를 반드시 피해야한다.

- 헤더파일에 선언되지 않은 함수들을 사용하는 경우 0점을 받는다.

- 각 헤더를 다른 헤더와 독립적으로 사용할 수 있어야 한다. 따라서 필요한 모든 종속성을 포함해야한다. 그러나 헤더가드를 사용해 이중으로 포함되는 것은 피해야만 한다. 그렇지 않으면 0점을 받을 것이다.

##### Read me

- 너는 필요(즉, 코드를 분할하기 위해)에 의해 파일을 추가할 수 있다. 이런 할당은 프로그램에서 확인하지 않으므로, 필수 파일을 제출하는 한 자유롭게 추가하면 된다.

- 시작 전에 꼭 모듈의 과제를 읽어야만 한다. 정말이다 !

> > ! 여기서 너의 업무는 STL 컨테이너를 다시 코딩하는 것이므로, 컨테이너 구현을 위해 STL 컨테이너를 사용할 수는 없다.

## Chapter 3

### Madatory part

다음 컨테이너들을 구현하고 Makefile과 함께 필요한 \<container>.hpp 파일을 제출한다:

- vector
