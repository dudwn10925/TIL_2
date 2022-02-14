[toc]



# matplotlib.pyplot

> import matplotlib.pyplot as plt



## 한글 설정

: matplotlib에서는 한글을 지원하지 않기 때문에 한글 설정이 필요

```python
# 런타임 초기화 --> 세 줄 실행 --> 런타임 다시 시작 --> 이후 셀 실행
!sudo apt-get install -y fonts-nanum
!sudo fc-cache -fv
!rm ~/.cache/matplotlib -rf

# 폰트, 마이너스 기호 설정
matplotlib.rcParams['font.family'] = 'NanumGothic'
matplotlib.rcParams['axes.unicode_minus'] = False
```



## 그리기

1. 바로 그리기
2. 여러 개 그리기
3. pandas객체를 통해 그리기