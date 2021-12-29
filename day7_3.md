# 파이썬 연습 5일차

#### 1. 문자열 매서드

```python
# 1. 기본 메서드 : 벡터 연산 불가 (매 원소마다 반복 불가)

'abc'.upper()
>>>
'ABC'

'a/b/c'.split('/')
>>>
'abc'

'a/b/c'.split('/')[1]
>>>
'b'

l1=['abc','def']
l2=['a/b/c','d/e/f']
l1.upper() # 리스트라 불가능
l2.split() # 리스트라 불가능

list(map(lambda x: x.upper(),l1))
>>>
['ABC', 'DEF']

list(map(lambda x: x.split('/'),l2))
>>>
[['a', 'b', 'c'], ['d', 'e', 'f']]
```



#### 2. Series, DataFrame

```python
# pandas 메서드 : 벡터화 내장(매 원소마다 반복 가능)
# Series, DataFrame

# 1) split

from pandas import Series, DataFrame

l1
>>>
['abc', 'def']

Series(l1)
>>>
0    abc
1    def
dtype: object

s1 = Series(l1)

l2
>>>
['a/b/c', 'd/e/f']

Series(l2)
>>>
0    a/b/c
1    d/e/f
dtype: object

s2 = Series(l2)

s2.str.split('/')
>>>
0    [a, b, c]
1    [d, e, f]
dtype: object

# 2) 대소 치환
s1
>>>
0    abc
1    def
dtype: object

s1.str.upper()
>>>
0    ABC
1    DEF
dtype: object
    
s1.str.lower()
>>>
0    abc
1    def
dtype: object
    
s1.str.title()
>>>
0    Abc
1    Def
dtype: object

# 3) replace
s1.str.replace('a','A')
>>>
0    Abc
1    def
dtype: object

s1.str.replace('a','') # 공백으로 만들기 매우 중요
>>>
0     bc
1    def
dtype: object

# 예제 - 천단위 구분기호 처리

s3 = Series(['1,200','3,000','4,000'])
s3.sum()
>>>
'1,2003,0004,000'
# 천 단위 구분기호 때문에 문자로 입력된 값이라 문자열 결합으로 인식됨
# 구분기호 문제네? 문자로 인식되어 있네? 더해줘야 되네

s3.str.replace(',','').astype('int').sum()
>>>
8200

s3 = Series(['1,200','3,000','4,000'])
s3= s3.str.replace(',','')
sum(list(map(lambda x: int(x), s3)))
>>>
8200
```



#### 3. 패턴 확인

```python
# startswith, endswith, contains

s1
>>>
0    abc
1    def
dtype: object

s1.str.startswith('a')
>>>
0     True
1    False
dtype: bool

s1[s1.str.startswith('a')] # s1 각 원소에서 'a'로 시작하는 원소 추출
>>>
0    abc
dtype: object

s1[s1.str.endswith('c')] # s1 각 원소에서 'c'로 끝나는 원소 추출
>>>
0    abc
dtype: object

s1[s1.str.contains('e')] # s1 각 원소에서 'e'를 포함하는 원소 추출
>>>
1    def
dtype: object
```



#### 4. 문자열

```python
# 문자열 크기 len()
s1.str.len()
>>>
0    3
1    3
dtype: int64

# count 포함 개수
Series(['aabbbb','abcdadd']).str.count('a')
>>>
0    2
1    2
dtype: int64

# 제거 함수 (공백, 문자)
Series(['       cd       ','        df        '])
>>>
0             cd       
1            df        
dtype: object

Series(['       cd       ','        df        ']).str.strip()
>>>
0    cd
1    df
dtype: object

Series(['       cd       ','        df        ']).str.strip().str.len()
>>>
0    2
1    2
dtype: int64

s1
>>>
0    abc
1    def
dtype: object

s1.str.strip('a') # 문자열 제거
Series(['aaaabaaabcd','asdfxaweabdaf']).str.strip('a') # 문자열 제거(중간값 삭제 불가)
>>>
0         baaabcd
1    sdfxaweabdaf
dtype: object
    
Series(['aaaabaaabcd','asdfxaweabdaf']).str.replace('a','') # 문자열 제거(중간값 삭제 가능)
>>>
0         bbcd
1    sdfxwebdf
dtype: object

# find(위치값 return)
s3 = Series(['abc@dwill.kr','abcdef@drwill.com'])
s3.str.find('@')
>>>
0    3
1    6
dtype: int64

# 문자열 색인(추출)
'abcde'[0:3]
s3
>>>
0         abc@dwill.kr
1    abcdef@drwill.com
dtype: object

s3[0:3]     # Series에서 1번째, 2번째, 3번째 원소 추출
>>>
0         abc@dwill.kr
1    abcdef@drwill.com
dtype: object

s3.str[0:3] # Series에서 각 원소마다 1번째, 2번째, 3번째 문자열 추출
>>>
0    abc
1    abc
dtype: object

# 이메일 아이디 추출
s4 = Series(['drwill@naver.com','zzuyu@drwill.kr'])
vemail = s4.str.find('@') # 위치정보
s4.str[0:vemail]
>>>
0   NaN
1   NaN
dtype: float64

list(map(lambda x, y : x[0:y], s4, vemail))
>>>
['drwill', 'zzuyu']

s4.map(lambda x : x[:x.find('@')])
>>>
0    drwill
1     zzuyu
dtype: object
```



#### 5. 문자열 삽입, 결합

```python
# pad : 문자열 삽입
s1.str.pad(5,       # 총자리수
           'Left',  # 삽입 방향
           '!')     # 삽입 글자

s1
>>>
0    abc
1    def
dtype: object

s1.str.pad(5, 'left', '!')
>>>
0    !!abc
1    !!def
dtype: object

s1.str.pad(5, 'right', '?')
>>>
0    abc??
1    def??
dtype: object

s5 = Series(["I love you","You know"])
s5
>>>
0    I love you
1      You know
dtype: object

s5.str.pad(20, 'right', '^')
>>>
0    I love you^^^^^^^^^^
1    You know^^^^^^^^^^^^
dtype: object

# 문자열 결합
'a' + 'b'
>>>
'ab'

'a'*3
>>>
'aaa'

s5 = Series(['abc','def','123'])
s5.str.cat()
>>>
'abcdef123'

s5.str.cat(sep=',')
>>>
'abc,def,123'

s5.str.cat(sep='/')
>>>
'abc/def/123'

s6 = Series([['a','b','c'],['d','e','f']])
s6
>>>
0    [a, b, c]
1    [d, e, f]
dtype: object

s6.str.join(sep='')     # Series 내 각 원소 내부의 문자열을 결합 (공백)
>>>
0    abc
1    def
dtype: object

s6.str.join(sep=',')    # Series 내 각 원소 내부의 문자열을 결합 (,)
>>>
0    a,b,c
1    d,e,f
dtype: object
```

