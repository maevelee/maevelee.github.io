---
title: "C언어 기초 - 함수"
excerpt: "C언어로 함수를 작성해보자."
categories:
  - lectures
tags:
  - Clang
last_modified_at:
---

## 함수

main 함수에 기능을 여러가지 넣는 것보다 함수로 기능을 분산시키는 것이 더 좋다.  
이제 한 번 C언어로 함수를 직접 만들어보자!  


## C언어 함수의 형태 

![](https://drive.google.com/uc?id=1QNE3F4R0wNvvqnx3KUtsR1Z3D_2wcm72){: width="40%" height="40%" .align-center}

c언어에서 함수는 위와 같은 구조를 가지고 있다. 

보다 더 잘 이해하기 위하여 두 정수를 덧셈하는 함수로 형태를 다시 한 번 살펴보자.  
  
```c
int Add(int num1, int num2) 
{
  int result = num1 + num2;
  return result;
}

// 반환 형태: int형 정수
// 함수명: Add
// 전달 인자: int형 정수 두 개 (num1, num2)
// 수행작업: 정수 두 개의 덧셈
```

이렇게 덧셈을 수행하는 함수만 놓고 보면 실제로 함수가 어떻게 작동하는지 잘 감이 안 잡히므로 (난 그랬다 ㅠㅇㅠ) main함수와 add함수를 연결시켜 작동 방식을 좀 더 자세히 살펴보자. 

```c
#include <stdio.h>

int Add(int num1, int num2) //덧셈 하는 함수. num1과 num2를 인자로 받는다. 
{
  int result = num1 + num2; //인자 두 개를 더하여 result변수에 값을 담는다. 
  return result; //result값을 반환한다. 
}

int main(void)
{
  int num1 = 0, num2 = 0; 

  printf("정수 두 개를 입력하세요: ");
  scanf_s("%d %d", &num1, &num2); //사용자로부터 값을 입력받는다. 
  printf("덧셈 결과는 %d 입니다.", Add(num1, num2)); //함수를 호출한다. 이 때, 함수명(인자)의 형식으로 호출해준다.

  return 0;
}
```
- - -

## 여러가지 함수의 형태

위 예시 코드를 통해 함수를 정복했다고 하면 참 좋겠지만 아쉽게도 아직 갈 길이 멀다.  
위에서 제시한 함수를 자세히 살펴보자.
```c
int Add(int num1, int num2)
```
이 Add 함수는 반환 형태가 int이다. 그리고, 인자로 int 자료형 num1, num2를 전달한다. 
그러나 위와 같은 함수도 있지만, **전달인자나 반환값이 존재하지 않는 함수**도 있다. 

아래 예시를 통해 전달인자나 반환값이 존재하지 않는 함수 형태를 한 번 살펴보자. 

```c
void ShowAddResult (int num)
{
  printf("덧셈 결과 출력: %d\n", num);
}
```
위 함수를 살펴보면 반환형태가 아까 작성한 Add 함수와 달리 void로 작성되어 있는 것을 확인할 수 있다.  

이 void에는 ***반환하지 않는다*** 라는 뜻이 담겨있다.
실제로 함수의 몸체 부분에 아까와 달리 return이 없는 것을 확인할 수 있다!


즉, 위 함수의 경우 인자는 전달하지만, 반환값을 전달하지 않는다. 

```c
int ReadNum(void)
{
  int num;
  scanf_s("%d", &num);
  return num;
}
```

위 함수의 경우 반환형태가 int형으로 되어 있어 반환값을 가진다. 그러나, 전달인자 부분에 void가 있는 것을 확인할 수 있다.  

즉, 위 함수는 인자를 전달하지 않고 반환값만 전달한다. 

```c
void HowToUseThisProg(void)
{
  printf("두 개의 정수를 입력하시면 덧셈결과가 출력됩니다.\n");
  printf("두 개의 정수를 입력하세요.");
}
```

위 함수는 반환형태와 전달인자가 모두 void로, 전달인자와 반환값이 모두 없는 경우이다.  
이렇게 전달인자와 반환값이 둘 다 없는 경우 단순 메세지 전달 함수이다. 

- - -

1. 전달인자와 반환값이 전부 있는 함수
2. 전달인자는 있으나 반환값이 없는 함수 
3. 전달인자는 없으나 반환값이 있는 함수  
4. 전달인자와 반환값이 전부 없는 함수  

위 네 가지 함수 형태를 모두 살펴보았으니 이제 이 네 가지 형태를 조합하여 정수 두 개를 덧셈하는 코드를 한 번 작성해보자! 

```c
int Add(int num1, int num2) //덧셈하는 함수
{
  return num1+num2;
}

void ShowAddResult (int num) //덧셈 결과를 출력하는 함수
{
  printf("덧셈 결과 출력: %d\n", num);
}

int ReadNum(void) //덧셈할 정수를 입력받는 함수
{
  int num;
  scanf_s("%d", &num);
  return num;
}

void HowToUseThisProg (void) //문자열을 출력하는 함수
{
  printf("두 개의 정수를 입력하시면 덧셈 결과가 출력됩니다.");
  printf("두 개의 정수를 입력하세요.");
}

int main(void)
{
  int result, num1, num2; //변수 설정

  HowToUseThisProg(); //문자열 출력
  num1 = ReadNum(); //첫 번째 정수 입력받기
  num2 = ReadNum(); //두 번째 정수 입력받기
  result = Add(num1, num2); //덧셈 연산한 값을 result변수에 담기
  ShowAddResult(result); //덧셈 결과 출력하기

  return 0;
}
```























