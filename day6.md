# 파이썬 연습 4일차



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
