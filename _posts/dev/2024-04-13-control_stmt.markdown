---
layout: post
title:  "[C언어] 8. 제어문(조건문, 분기문, 반복문)"
date:   2024-04-05 00:00:00 +0900
categories: dev develop
---
이번에는 C언어의 제어문(조건문, 분기문, 반복문)에 대해 알아보자.    

* toc
{:toc}

<br>
<br>
<br>

---
## **제어문(Control Statement)**
### **제어문이란**
**1) 제어문이란?** 순차적인 실행뿐만 아니라 선택과 반복 등 순차적인 실행을 변경하여 프로그램의 실행순서를 제어하는 문장     
<br>

**2) 제어문의 종류**
* **조건문(조건선택)** : 두 개 또는 여러 개 중의 하나를 선택하는 구조
* **분기분(분기처리)** : 정해진 장소로 이동하는 구조
* **반복문(반복)** : 반복 몸체인 여러문장을 반복하는 구조
<br>
<br>
<br>

---
## **조건문**
### **조건문이란?**
* 두 개 또는 여러 개 중에서 한 개를 선택하도록 지원하는 구문
* `if` `if else` `if else if` `switch` `nested if`

<br>
<br>

### **if문**
**1) if문 구조**

```c
if(cond)    //cond : 조건식
{
    stmt;
}

next;
```

* `cond 조건식`
    * 반드시 괄호 필요
    * `cond != 0(거짓)`이면 `stmt` 실행
* `stmt`
    * `cond`가 만족되면 실행되는 문장 
    * 여러문장이면 블록으로 구성, 들여쓰기 필수, 세미콜론으로 종료 

<br>

**2) if문 예시**

```c
//표준입력으로 받은 온도가 30도 이상이면 "폭염주의보를 발령합니다" 출력
//온도와 상관없이 항상 현재 온도 출력

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    double temp;

    printf("현재 온도를 입력하세요\n");
    scanf("%lf", &temp);

    if(temp >= 30.0)
        prtintf("폭엽주의보를 발령합니다.\n");

    printf("%현재온도는 lf 입니다.\n", temp);
    return 0;
}

```

<br>
<br>

### **if else문**
**1) if else문 구조**

```c
if(cond)
    stmt1;
else
    stmt2;

nest;
```

* `조건 cond`를 만족하면 `stmt1` 수행, 만족하지 않으면 `stmt2` 수행
* `cond 조건식` : 괄호 필수
* `stmt` : 실행문장이 여러줄이면 `{...}`

<br>

**2) if else문 예시**

```c
//표준입력으로 받은 정수가 짝수인지 홀수인지를 판별하는 프로그램
#define _CRT_SECURE_NO_WARNINGS
#inclue <stdio.h>

int main(void)
{
    int n;
    printf("정수를 입력하세요.");
    scanf("%d", &n);

    //if else문 이용
    if(n % 2)    //n % 2 != 0(홀수이면)
        printf("홀수\n");
    else
        printf("짝수\n");

    //조건연산자 이용
    (n % 2) ? printf("홀수\n"); : printf("짝수\n");
    return 0;
}
```

<br>
<br>

### **if else if문**

**1) if else if문 구조**

```c
if(cond1)
    stmt1;
else if(cond2)
    stmt2;
else if(cond3)
    stmt3;
else
    stmt4;

nest;
```

* 순서대로 조건을 충족하는지 확인하여, 조건을 충족하는 하나의 문장만 실행

<br>

**2) if else if문 예시**

```c
//평균 평점에 따른 적정 구문 출력

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main()
{
    double gpa;

    printf("평균평점 입력");
    scanf("%lf", &gpa);

    if(gpa >= 4.3)
        printf("최우등\n");
    else if(gpa >= 3.8)
        printf("우등\n");
    else if(gpa >= 3.0)
        printf("우수\n");
    else
        prinft("3.0 미만");

    return 0;
}

```

<br>

### **중첩된 if**
**1) 중첩된 if문 이란**
* 중첩된 if문 : if문 내부에 if문이 존재하는 것

```c
if(type == 1)
{    //없어도 오류는 없지만, 소스 가독성을 위해 삽입
    if(point >= 70)
        printf("1종면허 합격\n");
    else
        printf("1종면허 불합격\n");
}
else if(type == 2)
{
    if(point >= 60)
        printf("2종면허 합격\n");
    else
        printf("2종면허 불합격\n");
}
```

<br>
<br>

### **switch문**
**1) switch문 구조**

```c
switch(exp){
    case value1 :
        stmt1;
        break;
    case value2 :
        stmt2;
        break;
    case value3 :
        stmt3;
        break;
    default :
        stmt4;
        break;    //생략가능
}
```

* `exp` 결과 중 `case`의 값과 일치하는 항목의 문장 `stmti`를 실행한 후 `break`를 만나 종료
* `exp` : 결과값은 반드시 문자나 정수
* `value` : 상수식(constant expression), 중복X, 변수X
* `defalut` : 선택적이므로 사용하지 않을 수 있음, 어디에든 위치 가능
* `break` : switch문 바로 종료, break문을 만날 때 까지 실행

<br>

**2) switch문 예시**

```c
swtich(op)    //int op
{
    case 1 :
        printf("1번");
    case 2 :
        printf("2번");
    case 3 :
        printf("3번");
    default :
        printf("복권 당첨돼서 놀고 먹고 싶다");
}
```

```c
//오류발생
switch(month)
{
    case 4 : case 5 : 
        printf("봄");
        break;
    case 6, 7 :        //오류
        printf("여름");
        break;
}
```

```c
//연산식의 활용과 default의 위치

#define _CRT_SECURE_NO_WARNINGS
#inclue <stdio.h>

int main()
{
    int score;

    printf("점수를 입력하세요 : ");
    scanf("%d", &score);

    switch(score/10)
    {
        default:              //생략가능, 위치제한 없음
            printf("F");
            break;            //마지막에서만 생략가능
        case 10: case 9:
            printf("A");
            break;
        case 8:
            printf("B";
            break;
    }
    return 0;
}
```

<br>
<br>
<br>

---
## **분기문**
### **분기문이란**
* `break` : 작업을 수행하는 도중 조건에 따라 반복이나 선택을 빠져나감
* `continue` : 일정 구문을 수행하지 않고 다음 반복을 실행
* `goto` : 지정된 위치로 이동
* `return` : 작업 수행을 마치고 이전 위치로 돌아가는 구문

<br>
<br>
<br>

---
## **반복문**
### **반복문이란?**
**1) 반복문이란**
* 정해진 횟수나 조건을 만족하면 일정 영역의 문장을 여러 번 실행
* `while` `do while` `for`
<br>

**2) 반복문 개요**
* 반복(repetition) : 순환 = 루프, 같거나 비슷한 일을 여러 번 수행하는 작업
* 반복몸체(repetition body) : 반복조건을 만족하면 일정하게 반복되는 블록

### **while문**
**1) while문 구조**

```c
while(cond)
{
    반복몸체(loop body);
};
```

* `cond` : 반복조건
* 

<br>
<br>

### **do while문**
**1) do while문 구조**

```c
do
{
    반복몸체(loop body);
}
while(cond);
```

<br>
<br>

### **for문**
**1) for문의 구조**

```c
for(초기화; 반복조건; 증감)
{
    반복몸체(loop body);
}
```





<br>
