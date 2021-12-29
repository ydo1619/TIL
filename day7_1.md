# 파이썬 연습 5일차

#### 1. 사용자 정의 함수

```python
# 사용자가 정의하는 함수의 형태
# input과 output 관계를 내부에 정의
# def, lambda(축약형)

# 함수 정의
# f(x) = x + 1

# 1. def 방식

# def 함수이름(인수1, 인수2, 인수3):
#     함수 본문
#     return 반환할 객체

# 숫자를 넣어서 곱하기 10한 값을 반환

def f_mul(x):
    v1=x*10
    return v1

f_mul(100)
>>>
1000

# 두 숫자(두개의 인자를 넣구나!) 넣어서 두 숫자의 곱 반환

def f_2_mul(x,y):
    v2=x*y
    return v2

f_2_mul(2,10)
>>>
20

def f_d(x=1,y):                                            # 인수에 default 값 (기본값 선언)
    return(x*y)
>>>
SyntaxError: non-default argument follows default argument # 첫번째 인수에 기본값을 정의하면, 뒤에 나오는 인수도 기본값 정의해야함

def f_d(y, x=1):
    return(x*y)

def f_d(y=1, x=1):
    return(x*y)

print(f_d())
>>>
1
```



#### 2. lambda 축약형

```python
# 비교적 단순한 연산 및 리턴시 사용

# 예제 : 숫자를 넣을거에요. 여기에 10을 곱한 값을 리턴하세요

f1 = lambda x: x*10
f1(5)
>>>
50

# 문제
# 3개 숫자를 전달받아 첫 번째와 두번째 합에 세번째 숫자의 곱 리턴

f2 = lambda x,y,z : (x+y)*z
f2(2,3,4)
>>>
20
```



#### 3. map 함수

```python
f1=lambda x: x*10
f1(4)
>>>
40

l1=[1,2,5,10]
f1(l1)
# 리스트가 10번 반복

# 1) for문 처리
l2=[]
for i in l1:
    l2.append(i+10)
print(l2)
>>>
[11, 12, 15, 20]

# 연습해볼까요?
# 하나의 숫자를 전달받을거에요. 10보다 크면 3을 곱하고, 작거나 같으면 2를 곱한 결과를
# 리턴하시요

l2 = [3,5,7,9]

def f3(x):
    if x> 10:
        v1=x*3
    else:
        v1=x*2
    return v1

f3(11)
>>>
33

f3(5)
>>>
10

f3(l2) #error
>>>
TypeError: '>' not supported between instances of 'list' and 'int'     # list라 불가능

list(map(f3,l2))
>>>
[6, 10, 14, 18]
```