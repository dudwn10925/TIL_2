[toc]



# Pandas

> import pandas as pd

: 데이터 분석에 활용, NumPy 연산 가능

Series와 DataFrame 객체에 연산 가능



## Series

> pd.Series([ ], index=[ ])

: dictionary로 생성, dictionary와 다르게 객체에 연산이 가능, index를 지정하여도 숫자 indexing이 가능



#### 속성

index: 인덱스 반환

dtype: data type 반환

values: 요소 반환

str: string value에 접근		ex) str.len( ), str.contains( )



## DataFrame

> pd.DataFrame(list of list or dictionary, columns=[ ], index=[ ])

: Series의 모음



#### dataframe으로 읽기

`read_json()`: JSON 파일을 읽어 DataFrame 객체로 반환

`read_csv()`: CSV파일을 읽어 DataFrame 객체로 반환

`read_excel('~', skiprows=3)`: ' ~ '경로의 excel 파일에서 3줄을 skip하고 읽어옴



#### 속성, 함수

- index: 인덱스 반환

- columns: 칼럼 반환

- dtypes: 각 칼럼에 대한 data type 반환

- values: 요소 반환

- info( ): 객체에 대한 대략적인 정보 반환

- describe( ): 통계 자료 반환

- head( ), tail( ): 앞, 뒤 5행 반환

- isnull( ): 결측치 확인

- `sort_values('칼럼명', ascending=True, inplace=True)`: 칼럼을 기준으로 정렬, ascending은 오름차순

- `set_index('칼럼명')`: 해당 칼럼으로 index 설정

- count( ), sum( ), min( ), max( ): object 대상으로도 가능

- mean( ), median( ): 숫자형에만 가능

- `apply()`: 함수 적용

- `groupby()`: split --> apply --> combine

- unique( ): 속성의 고유값 추출

```python
# apply()
df['Population'] *= 1000
df['Population'].apply(lambda x: x*1000)

# groupby()
df.groupby('과목').mean()
```



#### 파일 변환

`to_json()`: JSON 파일로 변환

`to_csv('~')`: CSV 파일로 변환하여 ' ~ ' 파일로 저장

`to_excel()`: excel 파일로 변환

```python
# 엑셀 파일 시트별 저장
writer = pd.ExcelWriter('~.xlsx', engine='xlsxwriter')
df_iris1.to_excel(writer, sheet_name='iris1')
df_iris2.to_excel(writer, sheet_name='iris2')
writer.save()
```



#### 인덱싱과 슬라이싱

`iloc( , )`: integer location, 숫자로만 인덱싱 & 슬라이싱

`loc( , )`: label이 있다면 label로 인덱싱 & 슬라이싱, 슬라이싱 시 stop 부분도 포함됨에 주의

`at( , )`: 하나의 요소만 추출, 슬라이싱 불가

ex) 

df[ [ 'column1' , 'column2' ] ]		or		df[ 'column' ]

df[ 'index1' : 'index2']				# index2는 label이면 포함, integer면 불포함

행으로 인덱싱 할 시 슬라이싱으로 해야 함



#### 삭제

`drop([ , ], axis=0, inplace=False)`

inplace=True 라면 원본 데이터를 삭제
