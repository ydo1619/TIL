# 파이썬 연습 2일차

#### 1. CSV 파일에서 데이터 읽어오기 / 데이터 출력하기

```python
import csv
f = open('./data/seoul2.csv', 'r', encoding='cp949')
data = csv.reader(f, delimiter=',')
for row in data:
    print(row)
f.close()
>>>
['날짜', '지점', '평균기온(℃)', '최저기온(℃)', '최고기온(℃)']
['1907-10-01', '108', '13.5', '7.9', '20.7']
['1907-10-02', '108', '16.2', '7.9', '22']
```



#### 2. 헤더 저장하기

```python
import csv
f = open('./data/seoul2.csv', 'r', encoding='cp949')
data = csv.reader(f, delimiter=',')
header = next(data)
print(header)
f.close()
>>>
['날짜', '지점', '평균기온(℃)', '최저기온(℃)', '최고기온(℃)']
```



```python
import csv
f = open('./data/seoul2.csv', 'r', encoding='cp949')
data = csv.reader(f, delimiter=',')
header = next(data)
for row in data:
    print(row)
f.close()
>>>
['1907-10-01', '108', '13.5', '7.9', '20.7']
['1907-10-02', '108', '16.2', '7.9', '22']
['1907-10-03', '108', '16.2', '13.1', '21.3']
```



#### 3.  문자열 데이터를 실수 데이터로 변환

```python
import csv
f = open('./data/seoul2.csv', 'r', encoding='cp949')
data = csv.reader(f, delimiter=',')
header = next(data)
for row in data:
    row[-1] = float(row[-1]) # 최고 기온을 실수로 변환 row[-1] = row[4]
    print(row)
f.close()
>>>
['1907-10-01', '108', '13.5', '7.9', 20.7]
['1907-10-02', '108', '16.2', '7.9', 22.0]
['1907-10-03', '108', '16.2', '13.1', 21.3]
(생략)
['1950-08-29', '108', '23.1', '16.8', 30.4]
['1950-08-30', '108', '24.6', '18', 32.6]
['1950-08-31', '108', '25.4', '20.1', 32.5]
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
~\AppData\Local\Temp/ipykernel_7800/1891782376.py in <module>
      4 header = next(data)
      5 for row in data:
----> 6     row[-1] = float(row[-1])
      7     print(row)
      8 f.close()

ValueError: could not convert string to float: ''
```



#### 4.  대체할 특정값을 넣어 실수 데이터로 변환

```python
import csv
f = open('./data/seoul2.csv', 'r', encoding='cp949')
data = csv.reader(f, delimiter=',')
header = next(data)
for row in data:
    if row[-1] == '':
        row[-1] = -999 # -999를 넣어 빈 문자열이 있던 자리라고 표시
    row[-1] = float(row[-1])
    print(row)
f.close()
>>>
['1907-10-01', '108', '13.5', '7.9', 20.7]
['1907-10-02', '108', '16.2', '7.9', 22.0]
['1907-10-03', '108', '16.2', '13.1', 21.3]
(생략)
['1950-09-01', '108', '', '', -999.0]
['1950-09-02', '108', '', '', -999.0]
['1950-09-03', '108', '', '', -999.0]
(생략)
['2021-12-23', '108', '2.7', '-1.5', 8.3]
['2021-12-24', '108', '-0.3', '-7.3', 3.2]
['2021-12-25', '108', '-11.7', '-14.4', -7.3]
```



#### 5.  서울의 기온이 가장 높았던 날의 날짜와 기온 구하기

```python
import csv                                                # CSV 모듈 불러오기
f = open('./data/seoul2.csv', 'r', encoding='cp949')      # seoul2.csv 파일 읽기 모드로 불러오기
data = csv.reader(f, delimiter=',')
header = next(data)                                       # 맨 윗줄을 header 변수에 저장하기
max_temp = -999                                           # 최고 기온을 저장할 변수 초기화
mat_date = ''                                             # 최고 기온이었던 날짜를 저장할 변수 초기화
for row in data:
    if row[-1] == '':                                     # 만약 데이터가 누락되었다면 최고 기온을 -999로 저장
        row[-1] = -999
    row[-1] = float(row[-1])                              # 문자열로 저장된 최고 기온 값을 실수로 변환
    if max_temp < row[-1]:                                # 만약 지금까지 최고 기온보다 더 높다면 업데이트
        max_date = row[0]
        max_temp = row[-1]
f.close()                                                 # 파일 닫기
print('기상 관측 이래 서울의 최고 기온이 가장 높았던 날은', max_date + '로', max_temp, '도 였습니다.')       #출력
>>>
기상 관측 이래 서울의 최고 기온이 가장 높았던 날은 2018-08-01로 39.6 도 였습니다.
```

