---
layout: post
title:  "[C언어] 14. 구조체와 공용체"
date:   2024-04-30 00:00:00 +0900
categories: dev develop
---
이번에는 C언어의 구조체와 공용체에 대해 알아보자.    

* toc
{:toc}

<br>
<br>
<br>

---
## **구조체와 공용체**
### **구조체**
**1) 구조체란(structure)?**
* 정수나 문자, 실수, 포인터, 배열 등을 묶어 하나의 자료형으로 이용하는 것
* 대표적인 유도자료형(derived data types)

> 유도자료형
> - 사용자정의 자료형(user defined data type)
> - 구조체, 공용체, 열거형, 배열, 포인터

<br>

**2) 구조체 사용하기**
> 구조체 정의 -> 구조체 변수 선언 및 초기화

* 구조체 정의 : 변수 선언에서 이용될 새로운 구조체 자료형을 정의하는 구문
	* 구조체를 만들 구조체 틀(template) 정의
	* 구조체 멤버 : 일반변수, 포인터변수, 배열, 다른 구조체 변수 및 포인터

```c
/* 구조체 정의 */
struct 구조체태그이름
{	
	자료형 변수명;	//구조체 구성요소, 초기값 설정 불가능
	자료형 변수명;	//마지막 멤머에도 세미콜론 필수
};	//세미콜론 필수

struct student
{
	char name[20];		//이름
	int age, num;		//나이, 번호
	char birthday[11];	//생일
};

struct class
{
	struct student stu_info;
	char name;
}	
```

* 구조체 변수 선언

```c
//1. 구조체 정의 후 구조체변수 선언
struct 구조체태그이름 변수명;
struct 구조체태그이름 변수명1, 변수명2, 변수명3, ...;	//여러 변수의 선언도 가능

//2. 구조체 정의와 구조체변수 선언을 함께
struct student
{
	char name[20];		
	int age, num;		
	char birthday[11];	
} students;	//students는 struct student형 변수로 선언

//3. 이름없는 구조체
struct 
{
	char name[20];		
	int age, num;		
	char birthday[11];	
} students;	//students 이후에 동일한 구조체의 변수 선언은 불가능
```

<br>

* 구조체 변수 초기화     
	👉 변수 선언 시 중괄호를 이용한 초기화 가능    
	👉 중괄호 내부에서 구조체의 각 멤버 정의 순서대로 초기값을 쉼표로 구분하여 기술    
	👉 초기값이 기술되지 않은 멤버 값은 자료형에 따라 기본값 저장

```c
struct student
{
	char name[20];		
	int age, num;		
	char birthday[11];	
};

struct student student1 = {"부자지연이", 30. 1, 2030.01.10};
struct student student2 = {"지금지연이", 24, 1};	//birthday에는 '\0'

//.멤버이름 = 초기값으로 지정된 멤버에 초기값 저장 [C99]
struct student student3 = {.name ="핵부자지연이", .age = 32};
```

<br>

* 구조체 멤버 접근 연산자와 변수크기    
👉 `접근연산자(참조연산자) .`를 사용해 멤버 참조 가능

```c
구조체변수이름.멤버
mine.actnum = 1002;
mine.balance = 300000;

//이미 선언된 구조체 변수에 멤버 값 지정
struct account you;
you = (struct account) {.name = "김파이", .balance = 7000};
```

👉 실제 구조체의 크기 : 멤버의 크기의 합보다 크거나 같음

<br>

**3) 구조체 활용하기**
* 구조체 변수의 대입과 동등비교

```c
//동일한 구조체형 변수는 대입이 가능
struct goal one = {1, "편입시켜줘", "목표1"};
struct goal two = {2, "복권2등당첨시켜줘", "목표2"};
struct goal three = twol

//구조체 비교 - 멤버 하나하나 비교해야한다
if(one.num == two.num)
	printf("num가 같은 구조체입니다");

if(!(strcmp(one.content, two.content))	//문자열비교 : strcmp(인자, 인자);
	printf("내용이 같은 구조체입니다");
```

<br>
<br>

### **공용체 활용**
**1) 공용체란**
* 공용체 : 동일한 저장장소에 여러 자료형을 저장하는 방법
* 공용체를 구성하는 멤버에 한번에 한 종류만 저장하고 참조 가능

<br>

**2) union을 사용한 공용체 정의 및 변수 선언**
* 공용체 변수의 크기 : 멤버 중 가장 큰 자료형의 크기로 정해짐
* 모든 멤버가 동일한 저장공간을 사용해 마지막에 저장된 단 하나의 멤버 자료값만 저장
* typedef를 이용해 새로운 자료형으로 정의가능
* 공용체 정의 시 처음 선언한 멤버의 초기값으로만 초기화 가능

```c
union 공용체태그이름
{
	자료형 멤버변수명;	//공용체 구성요소(struct member)
	자료형 멤버변수명;
}[변수명1][,변수명2];	//세미콜론 필수

union data
{
	char ch;
	int cnt;
};

typedef union data uniondata;
	uniondata data2 = {'a'};
	//오류 - uniondata data2 = {1}
	uniondata data3 = data2;	//다른 변수로 초기화 가능
```

<br>

**3) 공용체 멤버 접근**
* `접근연산자 .` 이용
* 멤버 유형의 크기에 따른 공간 참조
* 마지막에 저장한 멤버의 참조만 가능

<br>
<br>
<br>

---
## **자료의 재정의**
### **자료형 재정의 typedaf**
**1) typedef 구문**
* typedef : 이미 사용되는 자료 유형을 다른 새로운 자료형 이름으로 재정의
* 프로그램의 시스템 간 호환성과 편의성을 위해 필요

```c
typedef 기존자료유형이름 새로운자료형, 새로운자료형;
typedef int profit;	//자료형이 int인 profit 자료형
```

<br>

### **구조체 자료형 재정의**

```c
struct date
{
	int year;
	int month;
	int day;
}

typedef struct date date;	//자료형이 struct date인 date자료형

//구조체 정의를 typedef와 함께 처리
typedef struct
{
	char title[30];
	char company[30];
	date release;
} software;	//software는 새로운 자료형
```

<br>
<br>
<br>

---
## **구조체와 공용체의 포인터와 배열**
### **구조체 포인터**
**1) 포인터 변수 선언**
* 구조체 포인터 : 구조체의 주소값을 저장하는 변수

```c
//구조체 선언
struct lecture
{
	char name[20];
	int type;
	int credit;
};

//구조체 포인터 변수 선언
typedef struct lecture lecture;
lecture *p;

//구조체 포인터 변수 사용
lecture os = {"운영체제", 2, 3};
lecture *p = &os
```

<br>

**2) 포인터변수의 구조체 멤버 접근연산자 >**
* `p -> name` : 포인터 p가 가리키는 구조체의 멤버 name
* `(*p).name` : 포인터 p가 가리키는 구조체의 멤버 name
* `*p.name` : 문법오류
* `os.name` : 
	* `*(os.name)`
	* 구조체 변수 os의 멤버포인터 name이 가리키는 변수
	* 구조체 변수의 해당 멤버의 첫 문자(한글이면 오류)
* `p->name` :
	* `(p->name)`
	* 포인터 p가 가리키는 구조체의 멤버 name이 가리키는 변수
	* 구조체 포인터 p가 가리키는 구조체 멤버의 첫 문자(한글이면 오류) 

<br>
<br>

### **공용체 포인터**
* 공용체 포인터 변수로 멤버 접근: 접근연산자 `->` 이용

```c
union data
{
	char ch;
	int cnt;
	double real;
}value, *p;

p = &value;
p->ch = 'a';
```

<br>
<br>

## **구조체 배열**

```c
lecture c[] = {
				{"인간과 사회", 0, 1},
				{"경제학개론", 1, 2},
				{"자료구조", 1, 4}
			  };

lecture *p = c;
```
