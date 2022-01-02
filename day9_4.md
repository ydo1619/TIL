# 파이썬 연습 7일차

#### 1. drop

```python
# 기타 메소드

import numpy as np
import pandas as pd
from pandas import Series, DataFrame

run my_modules
# 파일 my_modules에 저장되어있는 numpy, pandas(Series, DataFrame) 실행


# - 특정 행, 컬럼 제거
# - 이름 전달

emp = pd.read_csv("./data/emp.csv")
emp
>>>
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
4      5  scott      30  4100
5      6   king      20  4000

# scott 퇴사
emp.loc[emp['ename'] == 'scott'] # scott 관련된 record
>>>
   empno  ename  deptno   sal
4      5  scott      30  4100

emp['ename'] == 'scott' # 조건문
0    False
1    False
2    False
3    False
4     True
5    False
Name: ename, dtype: bool

emp.loc[emp['ename'] == 'scott',:]
>>>
   empno  ename  deptno   sal
4      5  scott      30  4100

emp.loc[~(emp['ename'] == 'scott'),:]
>>>
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
5      6   king      20  4000

emp.drop?
emp.drop(4, axis=0) # 행기준, 4번째 행 제거
>>>
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
5      6   king      20  4000

# [예제]
# emp 데이터셋에서 sal 컬럼 제외 (iloc)
emp.drop('sal', axis=1)
emp.iloc[:,0:3]
emp.iloc[:,:-1]
>>>
   empno  ename  deptno
0      1  smith      10
1      2  allen      10
2      3   ford      20
3      4  grace      10
4      5  scott      30
5      6   king      20

emp.loc[:, "empno":"deptno"]
>>>
   empno  ename  deptno
0      1  smith      10
1      2  allen      10
2      3   ford      20
3      4  grace      10
4      5  scott      30
5      6   king      20

emp.drop(['ename','deptno'], axis=1)
>>>
   empno   sal
0      1  4000
1      2  4500
2      3  4300
3      4  4200
4      5  4100
5      6  4000
```



#### 2. shift

```python
# - 행 또는 열을 이동
# - 전일자 대비 증감율

emp
>>>
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
4      5  scott      30  4100
5      6   king      20  4000

emp['sal'].shift()               # 'sal'열 첫번째 행에 NaN값을 넣어 한 행씩 밀리게 한다
>>>
0       NaN
1    4000.0
2    4500.0
3    4300.0
4    4200.0
5    4100.0
Name: sal, dtype: float64

# [예제 - 다음 데이터프레임에서 전일자 대비 증감율 출력]
s1 = Series ([3000,3500,4200,2800,3600], 
             index=['2021/01/01','2021/01/02','2021/01/03','2021/01/04','2021/01/05'])
s1
>>>
2021/01/01    3000
2021/01/02    3500
2021/01/03    4200
2021/01/04    2800
2021/01/05    3600
dtype: int64

# 1월 2일 증감율 >> (3500-3000)/3000
s1.shift()
>>>
2021/01/01       NaN
2021/01/02    3000.0
2021/01/03    3500.0
2021/01/04    4200.0
2021/01/05    2800.0
dtype: float64

(s1-s1.shift())/s1.shift() * 100
''''''
2021/01/01          NaN
2021/01/02    16.666667
2021/01/03    20.000000
2021/01/04   -33.333333
2021/01/05    28.571429
dtype: float64
```



#### 3. rename

```python
# - 행, 컬럼명 변경

emp
>>>
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
4      5  scott      30  4100
5      6   king      20  4000

emp.columns = ['emptno','ename','deptno','salary']
emp
>>>
   emptno  ename  deptno  salary
0       1  smith      10    4000
1       2  allen      10    4500
2       3   ford      20    4300
3       4  grace      10    4200
4       5  scott      30    4100
5       6   king      20    4000

emp.rename?

emp.rename({'salary':'sal','deptno':"dept_no"}, axis=1)
>>>
   emptno  ename  dept_no   sal
0       1  smith       10  4000
1       2  allen       10  4500
2       3   ford       20  4300
3       4  grace       10  4200
4       5  scott       30  4100
5       6   king       20  4000


# [예제] emp 데이터에서 ename을 index로 설정 후 scott를 대문자로 치환
emp_new = emp.set_index('ename')
emp_new
>>>
       emptno  deptno  salary
ename                        
smith       1      10    4000
allen       2      10    4500
ford        3      20    4300
grace       4      10    4200
scott       5      30    4100
king        6      20    4000

emp_new1= emp_new.rename({"scott":"SCOTT"}, axis=0)
emp_new1
>>>
       emptno  deptno  salary
ename                        
smith       1      10    4000
allen       2      10    4500
ford        3      20    4300
grace       4      10    4200
SCOTT       5      30    4100
king        6      20    4000
```

