[toc]



# NumPy

: 빠른 수치 연산

> import numpy as np



## ndarray

: N dimension array (다차원 배열)

> np.array( )로 생성



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
arr[1:2, 2]			# [6]
arr[1:2, [2]]		# [[6]]
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

- empty( ), empty_like( ), ones( ), ones_like( ), zeros( ), zeros_like( ), full( )
- identity( ), eye( )
- arange( ), linspace( )

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



#### np.random

`np.random.random( )`: 0 ~ 1 사이의 실수형 난수

`np.random.randint(a, b)`: a ~ b 사이의 정수형 난수

`np.random.rand(x, y)`: x행 y열 배열에 실수형 난수 채우기



#### !

```python
# web site
!wget -O '~' http:// ...
fromCSVArray = np.genfromtxt('~', delimiter=',')	# ndarray 객체로 반환
```

