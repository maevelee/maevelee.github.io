---
title: "C언어 기초 - 함수(2)"
excerpt: "C언어로 함수를 작성해보자."
categories:
  - lectures
tags:
  - Clang
last_modified_at:
---

## 함수를 main 함수 뒤에 놓는 방법

맨 위에 함수를 선언 부분을 입력해서 컴퓨터를 속이면 된다.

```c
int Increment (int n) //함수의 선언 부분을 코드의 위에 입력해준다.

int main(void) //main 함수를 작성한다.
{
    int num = 2;
    num = Increment(num);
    return n;
}

int Increment (int n) //앞에서 선언한 Increment함수를 작성한다.
{
    n++;
    return n;
}
```

이렇게 하면 컴퓨터가 "아~ 뒤에서 n이라는 int형 정수를 하나 받는 Increment함수가 나오니까 그냥 컴파일 해야겠다." 라고 생각하고 에러 없이 컴파일 해준다! 

## return문의 두 가지 의미 중 한 가지를 소거하기

Return문은값을 반환하면서 함수를 빠져나갈 때 사용된다. 
즉, Reutnr문은 다음 두 가지 의미를 지닌다.

1. 함수를 빠져나간다.
2. 값을 반환한다.

void로 선언된 함수에서도 (반환 값이 없지만) Return문을 사용할 수 있다. Return문이 함수를 빠져나가는 기능을 수행하기 때문이다.

아래 예시를 보자. 

```c
void NoReturnType(int num)
{
    if (num < 0)
     return; //값을 반환하지 않는 Return문
}
```
반환할 값을 명시하지 않았기 때문에 Return문이 가진 두 가지 의미 중 한 가지 의미만이 수행된다.  

따라서, 위 코드의 경우 값의 반환 없이 그냥 함수를 빠져나간다.

## 하나의 함수에 둘 이상의 return문이 존재하는 경우

하나의 함수에 둘 이상의 return문이 존재하는 경우 어떻게 코드를 작성해야 할까?

이런 경우 아주 간단하다. 그냥 return문을 두 번 써주면 된다. 

```c
#include <stdio.h>
int NumberCompare(int num1, int num2)

int main (void)
{
    printf("큰 수는 %d이다.", NumberCompare(3, 4));
    printf("큰 수는 %d이다.", NumberCompare(7, 2));

    return 0;
}

int NumberCompare (int num1, num2)
{
    if (num1 > num2)
     return num1; //num1을 Return
    else
     return num2; //num2를 Return
}
```

## 연습문제

1. 세 개의 정수를 인자로 전달받아 그 중 가장 큰 수를 반환하는 함수와 가장 작은 수를 반환하는 함수를 정의하라. 그리고 함수를 호출하는 함수를 작성하라.

```c
#include <stdio.h>

int biggestNum(int num1, int num2, int num3);
int smallestNum(int num1, int num2, int num3);

int num1 = 0, num2 = 0, num3 = 0;

int main(void)
{
	printf("세 개의 정수를 입력하세요. 가장 작은 수와 큰 수를 각각 반환합니다.\n");
	scanf_s("%d %d %d", &num1, &num2, &num3); //값 입력받기
	printf("입력한 숫자 중 가장 큰 수는 %d 입니다.\n", (biggestNum(num1, num2, num3))); //함수를 이용하여 값 출력
	printf("그리고 가장 작은 수는 %d 입니다.\n", (smallestNum(num1, num2, num3)));
	
	return 0;
}

int biggestNum(int num1, int num2, int num3) //가장 큰 수를 반환하는 함수
{
	if (num1 > num2 && num1 > num3)
		return num1; 
	else if (num2 > num1 && num2 > num3)
		return num2;
	else if (num3 > num1 && num3 > num2)
		return num3;
}

int smallestNum(int num1, int num2, int num3) //가장 작은 수를 반환하는 함수
{
	if (num1 < num2 && num1 < num3)
		return num1;
	else if (num2 < num1 && num2 < num3)
		return num2;
	else if (num3 < num1 && num3 < num2)
		return num3;
}
```

2. 섭씨를 입력하면 화씨 온도를 반환하는 CelToFah라는 이름의 함수를 정의하고, 그 반대를 수행하는 FahtoCel이라는 이름의 함수를 정의하라. 
두 함수를 호출하는 함수 역시 같이 작성한다.

```c
#include <stdio.h>

int CeltoFah(int temperature);
int FahtoCel(int temperature);

int choice = 0, temperature = 0;

int main(void)
{
	printf("섭씨/화씨 변환기\n");
	printf("1. 섭씨를 화씨로 변환\n 2.화씨를 섭씨로 변환\n");
	printf("수행할 작업을 선택하세요: ");
	scanf_s("%d", &choice);

	if (choice == 1) 
	{
		printf("섭씨 온도를 입력하세요: ");
		scanf_s("%d", &temperature);
		printf("%d의 화씨 온도는 %d도 입니다.", temperature, CeltoFah(temperature));
	}
    
	else if (choice == 2)
	{
		printf("화씨 온도를 입력하세요: ");
		scanf_s("%d", &temperature);
		printf("%d의 화씨 온도는 %d도 입니다.", temperature, FahtoCel(temperature));
	}
}

int CeltoFah (int temperature)
{
	int celToFah = (1.8 * temperature) + 32;
	return celToFah;
}

int FahtoCel (int temperature)
{
	int fahToCel = 1.8 / (temperature - 32);
	return fahToCel;
}
```
