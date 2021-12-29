# 파이썬 연습 5일차

#### 1. 논리연산자(and / or / not)

```python
v1=1
(v1>=3) and (v1<=7) # 3과 7 사이
>>>
False

(v1>=3) & (v1<=7)  # 3과 7 사이
>>>
False

(v1>=3) or (v1<=7)
>>>
True

(v1>=3) | (v1<=7)
>>>
True

not(v1==1)
>>>
False
```



#### 2. 조건문 if

```python
# 형식
# if 조건:
#     참(True)일 때 실행
# else:
#     거짓(False)일 때 실행 문장

# if 조건1:
#    조건1 참(True)일 때 실행
# elif 조건2:
#     조건1이 거짓(False)이면서 조건2가 참일 때 실행 문장
# else:
#     조건1, 2가 모두 거짓(False)일 때 실행 문장

v1=4

if v1>5:
    print('A')
else:
    print('B')
>>>
B

# 리스트는 불가
l1=[1,3,5,7,9]

if l1>5:
    print('A')
else:
    print('B')
>>>
TypeError: '>' not supported between instances of 'list' and 'int'
```



#### 3. 반복문

```python
# 객체의 각 원소에 동일한 연산처리 진행할 경우 사용
# 1.for 문 : 정해진 횟수, 대상이 있을 경우

# for 반복변수 in 반복할 대상(범위):
#     반복 실행할 문장

# 1~10 까지 출력하세요.
range(1,11)

for i in range(1, 11):
    print(i)
>>>
1
2
3
4
5
6
7
8
9
10

# 예제
# 다음의 리스트 선언하고 5보다 클 경우, 'A', 작거나 같을경우 'B'

l1 = [1,3,5,15,25]

for i in l1:
    if i>5:
        print('A')
    else:
        print('B')
>>>
B
B
B
A
A

# 위 리스트에서 각 원소에 10을 더해서 출력
l1 + 10 # 불가
>>>
TypeError: can only concatenate list (not "int") to list

for i in l1:
    print(i+10)
>>>
11
13
15
25
35

# for문의 결과를 변수로 저장하는 건 불가
l1 = for i in l1:
    print(i+10)
>>>
SyntaxError: invalid syntax

# 정답
l1 = [1,3,5,15,25]

l2 = []
for i in l1:
    l2.append(i+10)
    
print(l2)
>>>
[11, 13, 15, 25, 35]

l3 = [1,2,3]
l3.append(4)
l3
>>>
[1, 2, 3, 4]
```



#### 4. While 문 : 조건에 따른 반복을 실행하는 경우

```python
while 조건:
    조건이 참일 때 반복 문장
    
# 예제
# while 문으로 1~10까지 출력

i=1
while i <= 10:
    print(i)
    i = i+1
>>>
1
2
3
4
5
6
7
8
9
10

# 문제
# 1~100 까지 총 합

vsum = 0
for i in range(1,101):
    vsum = vsum + i
    
print(vsum)
>>>
5050

# 다른 방법(for문)
vvvv = sum(i for i in range(1,101))
print(vvvv)
>>>
5050
```



#### 5. 반복제어문

```python
# 반복제어문
# 1.continue : 특정 조건일 경우 반복문 스킵
# 2.break : 특정 조건일 경우 반복문 종료 (정지조건)
# 3.exit : 특정 조건일 경우 프로그램 종료
# 4.pass : 문법적으로 오류가 발생시키지 않게 자리를 채우는 역할

# 예제
# 1~10출력, 5제외

for i in range(1,11):
    if i == 5:
        continue
    print(i)
>>>
1
2
3
4
6
7
8
9
10
      
for i in range(1,11):
    if i == 5:
        break
    print(i)
>>>
1
2
3
4

v1=1
if v1 > 10:
    pass
else:
    print('b')
>>>
b

# 문제
# 1~100까지 누적합이 최초 2000 이상이 되는 시점의 k 값과 총 합을 출력하세요.

vsum=0
for i in range(1,101):
    vsum = vsum + i
    if vsum>=2000:
        break

print(i, vsum)
>>>
63 2016
```
