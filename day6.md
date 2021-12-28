# 파이썬 연습 4일차



## 책 따라해보기_01

### 서울의 기온 데이터 분석하기



#### 1. csv 파일에서 데이터 읽어오기 / 데이터 출력하기

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
['1907-10-03', '108', '16.2', '13.1', '21.3']
---생략---
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



#### 3. 헤더 값 이후 데이터 출력

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
['1907-10-04', '108', '16.5', '11.2', '22']
---생략---
```



#### 4. 최고 기온을 실수로 변환

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
['1907-10-04', '108', '16.5', '11.2', 22.0]
---생략---
```



#### 5. 빈 문자열 실수 입력

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
```



#### 6. 서울의 기온이 가장 높았던 날의 날짜와 기온 구하기

```python
import csv                                                    # CSV 모듈 불러오기
f = open('./data/seoul2.csv', 'r', encoding='cp949')          # seoul2.csv 파일 읽기 모드로 불러오기
data = csv.reader(f, delimiter=',')
header = next(data)                                           # 맨 윗줄을 header 변수에 저장하기
max_temp = -999                                               # 최고 기온을 저장할 변수 초기화
mat_date = ''                                                 # 최고 기온이었던 날짜를 저장할 변수 초기화
for row in data:
    if row[-1] == '':                                         # 만약 데이터가 누락되었다면 최고 기온을 -999로 저장
        row[-1] = -999
    row[-1] = float(row[-1])                                  # 문자열로 저장된 최고 기온 값을 실수로 변환
    if max_temp < row[-1]:                                    # 만약 지금까지 최고 기온보다 더 높다면 업데이트
        max_date = row[0]
        max_temp = row[-1]
f.close()                                                     # 파일 닫기
print('기상 관측 이래 서울의 최고 기온이 가장 높았던 날은', max_date + '로', max_temp, '도 였습니다.')         #출력
>>>
기상 관측 이래 서울의 최고 기온이 가장 높았던 날은 2018-08-01로 39.6 도 였습니다.
```

---



##  책 따라하기_02

### 내 생일의 기온 변화를 그래프로 그리기



#### 1. 기본 그래프 그리기

```python
import matplotlib.pyplot as plt

plt.plot([10,20,30,40])
plt.show

plt.plot([1,2,3,4],[10,23,34,45])
plt.title('multi_king!')                                       # 표 제목 설정
plt.show

plt.title('multi_king!')
plt.plot([1,2,3,4],[10,23,34,45], label='asc                   # 증가를 의미하는 asc 범례
plt.plot([1,2,3,4],[40,30,20,10], label='desc')                # 감소를 의미하는 desc 범례
plt.legend()                                                   # 범례 표시
plt.show()

plt.title('multi_king!')
plt.plot([1,2,3,4],[10,23,34,45], color='green', label='asc')  # 초록색 실선 그래프
plt.plot([1,2,3,4],[40,30,20,10], 'pink', label='desc')        # 분홍색 실선 그래프
plt.legend()
plt.show()

plt.title('maker')
plt.plot([1,2,3,4],[10,23,34,45], 'r.', label='circle')        # 빨간색 원형 마커 그래프
plt.plot([1,2,3,4],[40,30,20,10], 'b^', label='triangle_up')   # 파란색 삼각형 마커 그래프
plt.legend()
plt.show()
```



#### 2. 데이터 최고 기온 출력하기

```python
import csv
f = open('./data/seoul2.csv')
data = csv.reader(f)
next(data)

for row in data:
    print(row[-1])
    
>>>
20.7
22
21.3
22
```



#### 3. 데이터 리스트에 저장하기

```python
import csv
f = open('./data/seoul2.csv')
data = csv.reader(f)
next(data)
result = []                             # 최고 기온 데이터를 저장할 리스트 생성

for row in data :
    if row[-1] != '' :                  # 최고 기온 데이터 값이 존재한다면
        result.append(float(row[-1]))   # result 리스트에 최고 기온 값 추가
        
print(result)
>>>
[20.7, 22.0, 21.3, 22.0, 25.4, 21.3, 16.1, 14.9, 21.1, 24.1, 20.4, 17.4, 21.3, 20.6, 20.9, 20.2, 21.6, 20.9, 21.3, 22.7, 19.9, 19.6, 16.3, 17.1, 18.7, 18.2, 20.7, 19.6, 20.0, 20.1, 20.3, 21.3, 21.1, 11.1, 13.6, 17.0, 18.1, 12.4, 9.4, 11.9, 13.2, 13.4, 14.9, 16.4, 15.2, 17.6, 12.6, 11.7, 6.7, 4.3, 7.1, 6.2, 11.2, 9.9, 5.9, -0.7, 1.5, 1.9, 2.0, 2.9, -2.4, 1.4, 3.4, 6.1, 1.3, 2.6, 5.8, 1.9, 6.6, 8.1, ---생략---
```



#### 4. 데이터 시각화 하기

```python
import csv
import matplotlib.pyplot as plt

plt.plot(result,'r')
plt.show()
```



#### 5. 날짜 데이터 추출하기

```python
plt.show()s = 'hello python'
print(s.split())
>>>
['hello', 'python']

print(date.split('-'))
>>>
['1907', '10', '01']

print(date.split('-')[0])
print(date.split('-')[1])
print(date.split('-')[2])
>>>
1907
10
01
```



#### 6. 주어진 데이터에서 8월의 최고 기온 데이터 시각화하기

```python
for row in data :
    if row[-1] != '' :                         # 최고 기온 값이 존재한다면
        if row[0].split('-')[1] == '08' :      # 8월에 해당하는 값이라면
            result.append(float(row[-1]))      # result 리스트에 최고 기온 값 추가
            
plt.plot(result, 'hotpink')                    # result 리스트에 저장된 값을 hotpink 색으로 그리기
plt.show                                       # 그래프 나타내기
```



#### 7. 내 생일의 기온 변화를 그래프로 그리기

```python
import csv
import matplotlib.pyplot as plt

f = open('./data/seoul2.csv')
data = csv.reader(f)
next(data)
high = []                                                 # 최고 기온 값을 저장할 리스트 high 생성
low = []                                                  # 최저 기온 값을 저장할 리스트 low 생성

for row in data:
    if row[-1] != '' and row[-2] != '' :                  # 최고 기온 값과 최저 기온 값이 존재한다면
        date = row[0].split('-')                          # 날짜 값을 - 문자를 기준으로 구분하여 저장
        if 1991 <= int(date[0]) :                         # 1991년 이후 데이터라면
            if date[1] == '12' and date[2] == '15' :      # 12월 15일이라면
                high.append(float(row[-1]))               # 최고 기온 값을 high 리스트에 저장
                low.append(float(row[-2]))                # 최저 기온 값을 low 리스트에 저장
                
plt.rc('font', family='Malgun Gothic')              # 맑은 고딕을 기본 글꼴로 설정
plt.rcParams['axes.unicode_minus'] = False          # 마이너스 기호 깨짐 방지
plt.title('내 생일의 기온 변화 그래프')                 # 제목 설정

plt.plot(high, 'hotpink', label='high')             # high 리스트에 저장된 값을 hotpink 색으로 그리고 레이블을 표시
plt.plot(low, 'skyblue', label='low')               # low 리스트에 저장된 값을 skyblue 색으로 그리고 레이블을 표시

plt.legend()                                        # 범례 표시
plt.show()                                          # 그래프 나타내기
```
