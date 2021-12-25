# 파이썬 연습 1일차

```python
 names = ['쵸파', '루피', '상디', '조로']
names.append('해적왕')
for name in names:
    if len(name) > 2:
        print(name, '왔나요~?')
```


```python
print(34759**24341)

print('hello world')

name = '파이쏭'
print(name)

a = 1024
print(a)

print(name+'님! 안녕하세요!')

name = '원더키디'
print(2020, name, '화이팅!')

name = input()
print(name+'님 안녕하세요!')

name = input('이름을 입력해주세요 : ')
print(name+'님 안녕하세요!')

age = input('나이를 입력해주세요! : ')
print(int(age)-4)

name = input('이름을 입력해주세요 : ')
age = int(input('나이를 입력해주세요 : '))
print('안녕하세요', name+'님! 저는 처음에 ' +str(age - 4) + '살인 줄 알았어요!')
```



#### 산술 연산자

```python
print(3 * 10)
print(3 ** 10)
print (3 % 10)
print(3 / 2)
print(3 // 2)
```



#### 비교 연산자
```python
print(10 >= 3)
print(10 <= 3)
print(10 == 3)
print(10 != 3)
print(3 % 2 == 1)
```



#### 논리 연산자

```python
print(1 == 1 and 2 != 1)
print(10 % 2 != 0 and 1 + 1 > 0)

print(10 < 5 or 10 == 5)
print(10 % 2 != 0 or 1 + 1 > 0)

print(not 10 > 5)
print(not 10 == 5)
print(not 0)
print(not 10)
```



#### 함수 불러오기

```python
# random 숫자의 범위를 바꿔보세요

import random
dice = random.randint(1, 6)
print(dice)

import math
print(math.sqrt(2))
```




#### 반복과 선택
```python
name = '파이쏭'
for i in name:
    print(i)

names = ['쵸파', '루피', '상디', '조로']
for name in names:
    print(name)

for i in [0, 1, 2, 3] :
    print(i ** 2)

for i in range(100):
    print(i**100)

for i in range(100):
    print('나는 파이썬왕이 될 사람이다')


if 10 > 0 :
    print('안녕하세요')

if 10 != 0 and 5 % 2 ==1 :
    print('안녕하세요')
```

```python
passwd = int(input('비밀번호 4자리를 입력하세요 : '))
if passwd == 1531 :
    print('비밀번호가 일치합니다.')


for i in range(10000):
    if i == 1531:
        print('비밀번호가 일치합니다')

passwd = int(input('비밀번호 4자리를 입력하세요 : '))
if passwd == 1531 :
    print('비밀번호가 일치합니다')
else :
    print('비밀번호가 일치하지않습니다')
```

```python
print('[ 소름끼치도록 놀라운 심리테스트]')
menu = input('당신이 좋아하는 음식을 입력해주세요 : ')
if menu == '짜장면' :
    print('당신은 짜장면을 좋아하는 사람입니다.')
elif menu == '아이스크림' :
    print('당신은 아이스크림을 좋아하는 사람입니다.')
elif menu == '사탕' :
    print('당신은 사탕을 좋아하는 사람입니다.')
else :
    print('당신은 짜장면과 아이스크림과 사탕을 좋아하지 않는 사람입니다.')
```

​    

#### 순서 있는 저장 공간 리스트
```python
for i in [0, 1, 2, 3] :
    print(i ** 2)

names
for name in names :
    print(name)
    
print(names[1])

print(names[0])
print(names[1])
print(names[2])
print(names[3])

print(names[-1])

print(names[0:2])
print(names[1:3])
print(names[1:])
print(names[:])

names.append('나미')
print(names)

print(len(names))
print(len('data analysis for everyone'))

names = ['쵸파', '루피', '상디', '조로']
names.append('해적왕')
for name in names :
    if len(name) > 2 :
        print(name, '왔나요~?')
```