# 파이썬 연습 6일차_2

#### 1. 함수와 메서드

```python
# 함수 : 함수(대상)
# 메서드 : 대상.메소드
```



#### 2. 대소 치환

```python
v1 = 'abcde' #문자(string)
v1.upper() # 대문자 치환
>>>
'ABCDE'

'ABCDE'.lower() # 소문자 치환
>>>
'abcde'

'abc def'.title() # camel 표기법 (단어의 첫글자만 대문자로 표시)
>>>
'Abc Def'
```



#### 3. 색인(문자열 추출)

```python
'abcd'[0]
>>>
'a'

'abcd'[-2]
>>>
'c'

'abcd'[0:3]
>>>
'abc'

# ex) '031)345-0834' 에서 지역번호만 추출
vtel = '031)345-0834'
vtel[0:3]
>>>
'031'
```



#### 4. 문자열의 시작, 끝 여부 확인

```python
# v1.startswith(prefix, # 시작 값 확인 문자
#               start,  # 확인할 시작 위치 
#               end)    # 확인할 끝 위치

v1
>>>
'abcde'

v1.startswith('b')
>>>
False

v1.startswith('b', 1)
>>>
True

v1
>>>
'abcde'

v1.endswith('b')
>>>
False

v1.endswith('b', 1)
>>>
False
```



#### 5. 앞 뒤 공백 또는 문자 제거

```python
'abc' == 'abc'
>>>
True

' abc '.strip() # 양쪽 공백 제거
>>>
'abc'

'abc'.strip('a') # 문자 제거
>>>
'bc'

'abaca'.strip('a') # 양쪽 문자 제거(중간 글자 삭제 불가)
>>>
'bac'

' abcd'.lstrip() # 왼쪽 공백 또는 글자 제거
'abcd '.rstrip()
>>>
'abcd'
```



#### 6. 치환

```python
# 'abcde'.replace(old,   #찾을 문자열
#                   new) #바꿀 문자열

'abcde'.replace('a', 'A')
>>>
'Abcde'

'abcde'.replace('ab', 'AB')
>>>
'ABcde'

'abcde'.replace('ab', '')
>>>
'cde'
```



#### 7. 문자열 분리

```python
# v1.split(sep) # 분리 구분기호
'a/b/c/d'.split('/')
>>>
['a', 'b', 'c', 'd']

'a/b/c/d'.split('/')[1]
>>>
'b'

'a/b/c/d'.split('/')[0:2]
>>>
['a', 'b']
```



#### 8. 위치값 리턴

```python
# 'abcd'.find(sub,    # 위치값을 찾을 대상
#             start,  # 찾을 위치(시작점)
#             end)    # 찾을 위치(끝점)

v1
>>>
'abcde'

v1.find('b')
>>>
1

# ex. 전화번호 추출할려고 해요.
# ')' 위치를 확인해서 그 이전까지 추출하세요
vtel
>>>
'031)345-0834'

vnum=vtel.find(')')
vtel[0:vnum]
>>>
'031'

vtel[:vnum]
'031'
```



#### 9. 포함하는 횟수 / 형 확인 / 대소문자인지 확인

```python
# 포함하는 횟수
'abcabcabc'.count('a')
>>>
3

# 형 확인
v1
>>>
'abcde'

type(v1) # 데이터 타입 확인
>>>
str

v1.isalpha() # 문자 확인
>>>
True

v1.isnumeric() # 숫자 확인
>>>
False

# 대소문자인지 확인
v1.isupper() # 대문자 확인
>>>
False

v1.islower()
>>>
True
```



#### 10. 문자열 결합 / 길이

```python
# 문자열 결함
'a' + 'b'
>>>
'ab'

# 문자열 길이
len(v1)
>>>
5

3/len(v1)
>>>
0.6
```



#### 11. 연습

```python
vname='ydo1619'
vemail='ydo1619@naver.com'
jumin='123456-1123456'

# 1. 이름의 두번째 글자가 m인지 여부확인
vname[1] == 'm'
>>>
False

vname[1] == 'r'
>>>
False

# 2. vemail에서 이메일 아이디만 추출
vemail[0:7]
>>>
'ydo1619'

a=vemail.find('@')
vemail[:a]
>>>
'ydo1619'

# 3. 주민번호에서 여자인지 확인 (참고: 1: 남자, 2: 여자)

jumin
>>>
'123456-1123456'

jumin.split('-')[1][0] == 2
>>>
False

jumin[7] == '2'
>>>
False
```

