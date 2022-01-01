# 파이썬 연습 6일차

#### 1. replace 메서드_치환, 삭제

```python
# replace 메서드
# 치환(찾을 문자열, 바꿀 문자열)

# 1. 기본 문자열 메서드
# - 기본 파이썬 제공
# - 문자열에서 호출 가능
# - 벡터 연산(각 원소별 반복 처리) 불가
# - 오직 문자열 치환만 가능(숫자치환, NA 치환 불가능)

'abcd.'.replace('a',"A") # 'Abcd' >> a를 A로 치환
>>>
'Abcd.'

'abcd'.replace('a','')   # 'bcd' >> 공백으로 치환
>>>
'bcd'

'abcd1'.replace(1, '')   # 숫자를 찾아서 치환하는 거 안됨
>>>
TypeError: replace() argument 1 must be str, not int

' bcd1'.replace('', 1)
>>>
TypeError: replace() argument 2 must be str, not int

['abcd','abcde','aabb'].replace(',', '')
# AttributeError: 'list' object has no attribute 'replace'
# list는 replace 호출 불가

# for 문 활용

outlist = []
for i in ['abcd','abcde','aabb']:
    outlist.append(i.replace('a','A'))
    
print(outlist)
>>>
['Abcd', 'Abcde', 'AAbb']

# map함수
f1 = lambda x : x.replace('a', 'A')
list(map(f1,['abcd','abcde','aabb']))

['abcd','abcde','aabb'].map(f1)
# AttributeError: 'list' object has no attribute 'map'
# list 객체는 map 함수 호출 불가

from pandas import Series, DataFrame
['abcd','abcde','aabb'].map(f1) # 호출 불가
Series(['abcd','abcde','aabb']).map(f1)

# 0     Abcd
# 1    Abcde
# 2     AAbb
# dtype: object
```

