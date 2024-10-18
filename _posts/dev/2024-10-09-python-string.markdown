---
layout: post
title:  "[python] 1. 자료형 - 문자열 자료형"
date:   2024-10-09 00:00:00 +0900
categories: dev develop
---
이번에는 파이썬의 자료형 중 문자열 자료형에 대해 알아보자

* toc
{:toc}

<br>
<br>
<br>

---
## **파이썬 자료형**

### **자료형이란**
* 

<br>

### **파이썬 자료형의 종류**     
> `숫자` `문자열` `리스트` `딕셔너리` `튜플` `집합` `불`

<br>   
👉🏻 [숫자형 자료형](https://gangjiyeon.github.io/python-integer/)

<br>
<br>
<br>

---


## **문자열 자료형**
### **문자열 자료형(string) 이란**
* 연속된 문자열의 나열
* 예시
```
"Life is too short, You need Python"
"a"
"123"
```

<br>

### **문자열 자료형 사용하기**
**1) 문자열 자료형 만들기**
* 큰따옴표로 양쪽 둘러싸기 : `"Hello World"`
* 작은따옴표로 양쪽 둘러싸기 : `'Python is fun'`
* 큰따옴표 3개를 연속으로 써서 양쪽 둘러싸기 : `"""Life is too short, You need python"""`
* 작은따옴표 3개를 연속으로 써서 양쪽 둘러싸기 : `'''Life is too short, You need python'''`

<br>

**2) 작은 따옴표, 큰 따옴표 표현하기**
* 역슬래쉬 사용하기 : `'Python\'s favorite food is perl'`
* 문자열에 없는 따옴표(작은/큰) 사용하기 : `'"Python is very easy." he says.'`

<br>

**3) 여러 줄 문자열 표현하기**
* 줄바꿈 문자 `\n` 사용하기
* 큰/작은 따옴표 3개 사용하기

```py
multiline1 = "Life is too short\nYou need python"

multiline2='''
Life is too short
You need python
'''

multiline3="""
Life is too short
You need python
"""

print(multiline1)
print(multiline2)
print(multiline3)

# result
# Life is too short
# You need python

```

<br>

**4) 이스케이프 코드**
|코드|설명|
|:---:|---|
|`\n`|문자열 안에서 줄을 바꿀 때 사용|
|`\t`|문자열 사이에 탭 간격을 줄 때 사용|
|`\\`|\를 그대로 표현할 때 사용|
|`\'`|작은따옴표(')를 그대로 표현할 때 사용|
|`\"`|큰따옴표(")를 그대로 표현할 때 사용|
|`\r`|캐리지 리턴(줄 바꿈 문자, 커서를 현재 줄의 가장 앞으로 이동)|
|`\f`|폼 피드(줄 바꿈 문자, 커서를 현재 줄의 다음 줄로 이동)|
|`\a`|벨 소리(출력할 때 PC 스피커에서 '삑' 소리가 난다)|
|`\b`|백 스페이스|
|`\000`|널 문자|


<br>
<br>

### **문자열 연산하기**


