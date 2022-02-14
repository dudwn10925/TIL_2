[toc]

# Python(in vscode)



## Iterable 객체

#### list

a.`extend`(b): a를 b로 확장



#### tuple

: 수정 불가



#### set

> 생성: set()

intersection: 교집합 `&`

union: 합집합 `|`



#### string

문자열은 immutable, 변경 불가능하다



#### dictionary

> 생성: {}

key - value의 쌍

`get(key, "None")`: key에 대응되는 value 값 출력, key가 존재하지 않다면 None을 출력





## 파이썬 스타일 코드

#### list comprehension

```python
result1 = [i if i % 2 == 0 else 10 for i in range(10)]
result2 = [i for i in range(10) if i % 2 == 0]
```



#### enumerate

: 인덱스와 함께 unpacking

```python
for i, v in enumerate(['mango', 'watermelon', 'melon']):
    print(i, v)
```



#### filter

: iterable로부터 True만 추출

```python
# filter(function, iterable)
lst = [1, 2, 3, 4, 5, 6]
even = list(filter(lambda x: x % 2 == 0, lst))
print(even)		# [2, 4, 6]
```



#### map

: iterable의 요소를 함수에 적용시켜 반환

```python
# map(function, iterable)
ex = [1, 2, 3, 4, 5]
pow_ex = list(map(lambda x: x ** 2, ex))
print(pow_ex)		# [1, 4, 9, 16, 25]
```



#### reduce

: 시퀀스 자료형에 차례대로 함수를 적용하여 모든 값을 통합

```python
from functools import reduce
print(reduce(lambda x, y: x + y, [1, 2, 3, 4, 5]))
# 15, type: int
```



#### *, ** (asterisk)

- `*`: 가변 인수

  여러 개의 변수가 한번에 들어갈 수 있는 기능(tuple로 packing)

  iterable 객체 unpacking

- `**`: 키워드 가변 인수

  dictionary객체 packing or unpacking

```python
# 가변 인수
def asterisk_test(*args):
    print(args)
asterisk_test(*(2, 3, 4))		# (2, 3, 4)

# 키워드 가변 인수
def asterisk_test(**kargs):
    print(kargs)
asterisk_test(b=2, c=3, d=4)		# {'b': 2, 'c': 3, 'd': 4}

def asterisk_test(a, b):
    print(a, b)
data = {'a': 1, 'b': 2}
asterisk_test(**data)		# 1 2
```



## 파이썬 내장 함수

`abs()`: 절댓값

`all(iterable)`: 모두 True여야 True 반환

`any(iterable)`: 하나만 True여도 True 반환

chr(num): num의 아스키코드 값

ord('ch'): ch의 ordinal number

dir(obj): obj에 적용할 수 있는 변수 or 함수 목록

`divmod(a, b)`: (a//b, a%b)

eval(' ~ '): ~ 의 연산 수행

`hex(), oct()`: 16진수, 8진수

`id()`: 객체 메모리 상의 주소

`input()`: 입력, str로 반환

`isinstance(a, b)`: a가 b의 객체느냐

pow(a, b): a ** b

`round()`: 반올림

`sorted(iterable)`: 정렬하여 list로 반환

`zip()`: 같은 인덱스끼리 묶어 tuple로 반환

```python
all({})			# True
all((2, ))		# True
any([])			# False
dir(int)
dir('')
eval("'hi' + 'a'")		# 'hia'
eval('divmod(7, 3)')

a = list(zip(*[[1, 2, 3], [4, 5, 6]]))
print(a)		# ((1, 4), (2, 5), (3, 6))
```



 ## 암묵적 False

- 0
- None
- ""  / " " (공백이 있다면 True)



## `__name__`

```python
if __name__ == '__main__':		# 1
    print('running in direct file')

if __name__ == 'mod.mod2':		# 2 (이 코드는 mod.mod2에 존재)
    print('activate mod.mod2.py')
```

1. 이 코드가 있는 파일을 직접 실행할 시 `__name__ = '__main__'`
2. 'mod.mod2' 모듈 파일을 import한 파일을 실행하면 `__name__ = 'mod.mod2'`



## import sys

#### sys.argv

: vscode TEMINAL창에서 `python <파일명> sys.argv[1] sys.argv[2] ...`



#### sys.path.append

- path: 환경 변수(시스템 변수)

```python
# mod파일에 있는 mod2 모듈 파일을 import
import sys
sys.path.append('C:\workspace\mod')
import mod2
```

또는 TERMINAL창에 `set PYTHONPATH='C:\workspace\mod'` 입력 후 import mod2



#### sys.stdin.readline

```python
import sys
input = sys.stdin.readline
```



## 예외 처리

#### 형식

```python
try:
    예외가 발생할 것 같은 실행문
except:
    예외 처리
else:
    예외가 발생하지 않았을 때 실행
finally:
    무조건 실행
```



#### 사용자 정의 예외 처리(`__str__`의 사용)

```python
# 사용자 정의 예외 처리
class MyError(Exception):
    def __str__(self):
        return '영주는 바보가 아니다'

def say_nick(nick):
    if nick == '바보':
        raise MyError		# raise: 일부러 exception 발생

say_nick('바보')
```



## 데이터 저장

#### 파일(파일 복사, 임시 파일 만들기)

- 읽기

  `f.read()`: 파일 전체 내용을 str로 읽음

  `f.readline()`: 파일 내용 한 줄씩 str로 읽음(while문 활용)

  `f.readlines()`: 파일 전체 내용을 list로 반환

- 쓰기

  `f.write(data)`: 파일에 data 저장

- 인코딩

  encoding='utf8' or 'cp949'

```python
# 파일 복사
import shutil
shutil.copy('text1.txt', 'text2.txt')

# 임시 파일 만들기
import tempfile
f = tempfile.mkstemp()
print(f)
```



#### pickle 객체

```python
# pickle: 문자열 외의 데이터 저장 or 읽음
import pickle

class Multiple_:
    def __init__(self, multiplier):
        self.multiplier = multiplier
    def multiply(self, number):
        return number * self.multiplier
m = Multiple_(5)

with open('pickle_test.txt', 'wb') as f:	# wb: write binary
    data = {1: 'python', 2: 'javascript'}
    data1 = 'youngju'
    pickle.dump(data, f)
    pickle.dump(data1, f)
    pickle.dump(m, f)
    
lst = list()
with open('pickle_test.txt', 'rb') as f:
    while True:
        try:
            msg = pickle.load(f)
            if isinstance(msg, Multiple_):
                print(f'Multiple_객체를 만났습니다.\n연산의 결과는 {msg.multiply(2)}입니다.\n)
            lst.append(msg)
        except:
            break
                      
print(lst)
```

`pickle.dump(data, f)`: 데이터를 f 파일에 저장

`pickle.load(f)`: f 파일의 데이터를 하나씩 읽어옴



## Module

: 특정 기능을 수행하는 하나의 단위



#### random

`random.random()`: 실수형 난수

`random.randint(a, b)`: a~b에서 정수형 난수

`random.choice(list)`: list에서 무작위로 요소 선택

`random.shuffle(list)`: list 섞기

`random.sample(range(a, b), k)`: 중복되지 않게 정수형 난수 k개 추출



#### 그 외의 모듈들

```python
# webbrowser
import webbrowser
webbrowser.open('http://google.com')

# calendar
import calendar
print(calendar.calendar(2022))		# calendar.prcal(2022)
print(calendar.prmonth(2022, 1))
print(calendar.weekday(2022, 2, 3))
print(calendar.monthrange(2022, 2))	# (2월의 시작 요일, 며칠까지 있는지)

# os
import os
print(os.environ['path'])		# 환경 변수
os.chdir(os.getcwd() + '\lib')	# change dir, get current working dir

print(os.system('dir'))		# dir목록이 보이기는하나 실제 반환값이 아님
f = os.popen('dir')
print(f.read())				# 실제 반환값이 dir목록
f = os.popen('code')
print(f.read())				# vscode 실행

# time
# "strftime.org" 참조
import time
print(time.asctime(time.localtime(time.time())))	# 시간 변환
print(time.strftime('%c'))	# 시간 포맷
for i in range(5):
    print(time.ctime())
    time.sleep(2)
    
# datetime
import datetime
datetime.datetime.now()		# 현 시각 추출
```



## 리눅스 명령어 `!`

```python
# web site
!wget -O '~' http:// ...
fromCSVArray = np.genfromtxt('~', delimiter=',')		# ndarray로 반환

# 엑셀 라이브러리 설치
!pip install xlsxwriter

# MYSQL Client Library 설치
!pip install mysql-connector-python

# ImportError: 엑셀 읽기 에러
!pip install --upgrade xlrd
```

`'~'` 부분에 `.csv`로 하면 csv 파일로, `.txt`로 하면 txt 파일로 저장됨
