---
layout: post
title:  "[python] 2. 자료형 - 문자열 자료형"
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
```py
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
**1) 문자열 더하기**
```py
head = "python"
tail = "is fun"

print(head + tail)  # result = python is fun
```

**2) 문자열 곱하기**
```py
str = "hello boo~"
print(str * 2)    # result : hello boo~hello boo~
```

<br>
<br>

### **문자열 길이 구하기**
* 문자열 길이 구하기 : `len(문자열)`
* 문자열 길이에는 공백 문자도 포함
```py
a = "life is too short"
print(len(a))  # result : 17
```

<br>
<br>

### **문자열 인덱싱과 슬라이싱**
**1) 문자열 인덱싱과 슬라이싱이란**
* 인덱싱(indexing) : 무엇인가를 가리킨다

```py
a = "Life is too short, You need Python"

print(a[3])  # result : e, 인덱스 번호의 시작은 0
print(a[-1])  # result : n, 뒤에서 첫번째 문자
print(a[-0])  # result : L, 뒤에서 0번째 문자
print(a[0])  # result : L, 앞에서 0번째 문자
```

* 슬라이싱(slicing) : 무엇인가를 잘라낸다

```py
# 사용법
# 문자열[시작:종료(미만)]
# 시작 기본값 : 처음
# 종료 기본값 : 끝
a = "Life is too short, You need Python"

print(a[0:4])  # result : Life
print(a[19:])  # result : You need Python
print(a[:17])  # result : Life is too short
print(a[:])    # result : Life is too short, You need Python
```



<br>
<br>

### **문자열 포매팅**
* 문자열 포매팅(stringi formatting) : 문자열 안에 어떤 값을 삽입하는 방법
* `"%[정렬][공백][.소숫점]포맷코드" % 값`
<br>

**1) 문자열 포맷 코드**

|코드|설명|
|:---:|:---:|
|`%s`|문자열(String)|
|`%c`|문자 1 개(character)|
|`%d`|정수(Integer)|
|`%f`|부동소수(floating-point)|
|`%o`|8진수|
|`%x`|16진수|
|`%%`|Literal %(문자 `%` 자체)|

```py

# 숫자 대입
a = "I eat %d apples." % 3
print(a)  # result : I eat 3 apples.

num = 3
b = "I eat %d apples." & num
print(b)  # result : I eat 3 apples.
```

<br>

```py
# 문자 대입
a = "I eat %s apples." % "two"
print(a)  # result : I eat two apples.

str = "two"
b = "I eat %s apples." % str
print(b)  # result : I eat two apples.

# %s 포맷코드에는 어떤 형태의 값이든 변환해 넣을 수 있다.
c = "I eat %s apples." % 3
print(c)  # reuslt : I eat 3 apples
d = "I eat %s apples." % 3.14
print(d)  # I eat 3.14 apples.
```

<br>

* 여러 값 넣기
```py
num = "ten"
day = 3
print(I ate %s apples. so I was sick for %d days. % (num, day))
# result : I ate ten apples. so I was sick for 3 days.
```

<br>

**2) 정렬**
* 오른쪽 정렬 : `default`
* 왼쪽 정렬 : `-`

### **문자 관련 함수들**
> 값을 바꾸어 리턴할 뿐, 실제 문자열이 바뀌지는 않는다

**1) 문자 개수 세기 `count()`**
* `문자열.count('문자") : 문자열에 포함된 문자의 갯수 반환`
```py
a = "hobby"
a.count("b:")  # 2
```

<br>

**2) 위치 알려 주기 `find()` `index()`**
* `문자열.find('문자(열)')`
  * 문자열에서 처음으로 해당 문자(열)가 나온 위치 반환
  * 찾는 문자(열)가 존재하지 않으면 -1 반환
* `문자열.index('문자(열)')`
  * 문자열에서 처음으로 해당 문자(열)가 나온 위치 반환
  * 찾는 문자(열)가 존재하지 않으면 오류 발생

```py
a = "Python is the best choice"
a.find('b')  # 14
a.find('k')  # -1

a = "Life is too short"
a.index('t')  # 8
a.index('k')  # error
```

<br>

**3) 문자열 삽입 `join()`**
* `"삽입문자".join('문자열")` : 삽입문자를 문자열의 각 문자 사이에 삽입

```py
",".join('abcd')  # 'a,b,c,d'

",".join(['a', 'b', 'c', 'd'])  # 'a,b,c,d'
```

<br>

**4) 대소문자 바꾸기**
* 소문자를 대문자로 바꾸기 `upper()`
* 대문자를 소문자로 바꾸기 `lower()`

```py
a = "hi"
a.upper()  # 'HI'

a = "HI"
a.lower()  # 'hi'
```

<br>

**4) 공백지우기**
* 왼쪽 공백 지우기 `lstrip` : 문자열 중 가장 왼쪽에 있는 한 칸 이상의 연속된 공백들을 모두 지운다
* 오른쪽 공백 지우기 `rstrip` : 문자열 중 가장 오른쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다
* 양쪽 공백 지우기 `strip` : 문자열 양쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다

```py
a = " hi "
a.lstrip()  # 'hi '

a= " hi "
a.rstrip()  # ' hi'

a = " hi "
a.strip()  # 'hi'
```

<br>

**5) 문자열 바꾸기 `replace`**
* `replace(바뀔문자열, 바꿀문자열)`

```py
a = "Life is too short"
a.replace("Life", "Your leg")  # 'Your leg is too short'
```

<br>

**6) 문자열 나누기 `split`**
* `문자열.split('구분자')`
* 구분자 기본 값 : 공백(space, tab, enter)
* return 값 : 리스트


```py
a = "Life is too short"
a.split()  # ['Life', 'is', 'too', 'short']

b = "a:b:c:d"
b.split(':')  # ['a', 'b', 'c', 'd']
```












