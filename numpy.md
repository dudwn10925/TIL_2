[toc]



# NumPy

> import numpy as np

: 빠른 수치 연산



## ndarray

> np.array( )로 생성

: N dimension array (다차원 배열)

0차원: scalar, 1차원: vector, 2차원 이상: array



#### indexing & slicing

> arr[row, col]

```python
arr = np.arange(1, 13).reshape(4, 3)
#	[
#	    [1, 2, 3],
#	    [4, 5, 6],
#	    [7, 8, 9],
#	    [10, 11, 12]
#	]

arr[[0, 2], ]		# [[1, 2, 3], [7, 8, 9]]
arr[0, 2]			# 3
arr[1][2]			# 6
arr[[0, 2], [0, 0]]	# [1, 7]
arr[1:2, 2]			# [6]
arr[1:2, [2]]		# [[6]]
arr[3:][1:]			# [ ], ndim=2
arr[3:, 1:]			# [[11, 12]]

arr_idxing = arr[0, 0]
arr_idxing = 100	# arr 변경 없음
arr_slicing = arr[2:, 1:]
arr_slicing[0, 0] = 100		# arr 변경됨
```

indexing을 할수록 차원이 줄어든다 but `[ ]`로 indexing을 한다면 차원이 유지된다



## broadcasting

: 한번에 모든 요소를 연산



## 다양한 기능(함수 등)

---> `np.`으로 진행할 것

- max( )=amax( ), min( )=amin( ), sum( ), mean( ) , average( ), var( ): 분산, std( ): 표준편차,

  ptp( ): 최댓값-최솟값, median( ): 중앙값

  - axis

    0: 행, 세로

    1: 열, 가로

- add( ), subtract( ), multiply( ), divide( ), sqrt( )

- empty( ), empty_like( ), ones( ), ones_like( ), zeros( ), zeros_like( ), full( )

- identity( ), eye( )

- arange( ), linspace( )

- concatenate((a, b), axis=0)

- tile(a, (x, y)): a를 하나의 요소로 보고 x행 y열로 맞추기

- repeat(x, a): x객체를 a번 반복하여 1차원 배열로 반환

- trim_zeros( ): 앞뒤의 0을 제거

- cumsum(axis=0): 누적합

- bincount( ): ndarray의 index 빈도수

- c_[a, b]: a와 b를 column을 기준으로 배열

```python
# mean(): 산술 평균
np.mean(range(1, 11))

# average(): 산술 평균 or 가중 평균
np.average(range(1, 11), weights=range(10, 0, -1))
range(10, 0, -1)	# 10, 9, 8, ... , 1

# identity(), eye(): 항등 행렬
np.eye(3, 3, -1)		# [[0, 0, 0],
						#  [1, 0, 0],
						#  [0, 1, 0]]
        
# linspace()
np.linspace(2.0, 3.0, num=5)	# 2.0 ~ 3.0 사이에 일정한 간격으로 5개 값 추출
```

가중 평균: 같은 인덱스에 대한 가중치를 곱하여 모두 합산한 뒤 가중치의 전체 합으로 나눈다



#### NumPy 객체에..

tolist( ): list로 변환

strides: (행 간의 차이값, 열 간의 차이값)

shape: 형태 반환

size: 크기 반환

ndim: 차원

T: transpose, 전치행렬, 1차원은 불가

ravel( ), flatten( ): 1차원 배열, np.ravel( )도 가능

dot( ): 내적



#### np.random

`np.random.seed()`: seed값 설정, 고정된 난수 생성 위함

`np.random.random()`: 0 ~ 1 사이의 실수형 난수

`np.random.randint(a, b)`: a ~ b 사이의 정수형 난수

`np.random.rand(x, y)`: x행 y열 배열에 0 ~ 1 사이의 실수형 난수 채우기

`np.random.randn(x, y)`: x행 y열 배열에 음수를 포함한 실수형 난수 채우기

`np.random.uniform(a, b, x)`: a ~ b 사이의 실수형 난수 x개 추출
