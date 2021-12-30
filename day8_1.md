# 파이썬 연습 6일차

#### 1. Pandas _ Series, DataFrame

```python
import numpy as np
from pandas import Series, DataFrame

df1 = DataFrame(np.arange(1,17).reshape(4,4))
>>>
    0   1   2   3
0   1   2   3   4
1   5   6   7   8
2   9  10  11  12
3  13  14  15  16

dir(df1)

df1.sum(axis=0) # 행별(서로 다른 행끼리) |
>>>
0    28
1    32
2    36
3    40
dtype: int64

df1.sum(axis=1) # 컬럼별(서로 다른 열끼리) ㅡ
>>>
0    10
1    26
2    42
3    58
dtype: int64

df1.iloc[:,0].sum()
>>>
28

df1.iloc[:,0].mean()
>>>
7.0

df1.iloc[0,0] = np.nan
>>>
      0   1   2   3
0   NaN   2   3   4
1   5.0   6   7   8
2   9.0  10  11  12
3  13.0  14  15  16

df1.iloc[:,0].mean() # skipna = True (default) 자동으로 NaN 무시하고 연산
>>>
9.0

# 평균값(최대 또는 최소) 대치

df1.iloc[:,0].mean()
df1.iloc[:,0].isnull()      # 조건(boolean)
>>>
0     True
1    False
2    False
3    False
Name: 0, dtype: bool

df1.iloc[:,0][df1.iloc[:,0].isnull()] = df1.iloc[:,0].mean()

df1[df1.isnull()]       # 데이터프레임 전체에서 NaN 값 확인
>>>
    0   1   2   3
0 NaN NaN NaN NaN
1 NaN NaN NaN NaN
2 NaN NaN NaN NaN
3 NaN NaN NaN NaN

df1[df1.notnull()]
>>>
      0   1   2   3
0   9.0   2   3   4
1   5.0   6   7   8
2   9.0  10  11  12
3  13.0  14  15  16

df1.iloc[:,0].var()     # 분산
>>>
10.666666666666666

df1.iloc[:,0].std()     # 표준편차
>>>
3.265986323710904

df1.iloc[:,0].min()     # 최소값
>>>
5.0

df1.iloc[:,0].max()     # 최대값
>>>
13.0

df1.iloc[:,0].median()  # 9.0 >> 중위수(중앙값)
>>>
9.0

(df1.iloc[:,0] >= 10).sum()     # 1 >> 조건에 만족하는 개수 확인
# 0    False
# 1    False
# 2    False
# 3     True
# Name: 0, dtype: bool
```

