[toc]



# Pandas

> import pandas as pd

: 데이터 분석에 활용



## Series

> pd.Series([ ], index=[ ])

: dictionary로 생성, dictionary와 다르게 객체에 연산이 가능, index를 지정하여도 숫자 indexing이 가능

index: 인덱스 반환

dtype: data type 반환

values: 요소 반환



## DataFrame

> pd.DataFrame(list of list or dictionary, columns=[ ], index=[ ])

: Series의 모음, index를 지정하면 숫자 indexing이 불가

index: 인덱스 반환

columns: 칼럼 반환

dtypes: 각 칼럼에 대한 data type 반환

values: 요소 반환

info( ): 객체에 대한 대략적인 정보 반환

set_index('칼럼명'): 해당 칼럼으로 index 설정