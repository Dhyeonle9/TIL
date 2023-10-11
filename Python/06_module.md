# 모듈
- 함수나 변수 또는 클래스를 모아 놓은 파이썬 파일
- 모듈은 다른 파이썬 프로그램에서 불러와 사용할 수 있음
- `.py 확장자` 사용
- 사용 예
    ```python
    import 모듈명 
    import 모듈명 as 별칭 # 불러온 모듈을 별칭으로 지정
    from 모듈 import 함수/클래스
    from 모듈 import * # import * 모두 불러옴, 메모리때문에 잘 사용하지않음

    import random as rd

    b = [1, 2, 3, 4, 5]
    rd.shuffle(b) # rd라고 지정한 random 모듈의 shuffle 함수 실행

    ```

## 패키지
- 여러 개의 모듈을 그룹화한 것으로 라이브러리라고도 함
- 패키지 안에 `__init__.py`파일이 있어야 패키지로 인식
- 패키지 형식
    ```python
         myPackage/
            __init__.py
            math/
                __init__.py
                fibo.py
                fomula.py
    ```
- 사용 예
    ```python
    import 패키지
    from 패키지(or 디렉토리) import 모듈


    import myPackage
    from myPackage.math import fomula

    fomula.pi
    ```

## 파이썬 내장 패키지
### math
수학 함수
```python
import math
math.pi # pi
> 3.141592653589793
math.e # 자연상수
> 2.718281828459045
math. ceil(pi) # 올림
> 4
math.floor(pi) # 내림
> 3
math.sqrt(9) # 루트
> 3.0
math.factorial(10) # 팩토리얼
> 362880
```
### random
랜덤함수
```python
import random
random.random() # 0~1까지 무작위 수 추출
random.randint(1, 10) # 1부터 10까지의 수 중 랜덤으로 추출

# 랜덤함수는 가짜난수를 생성(Pseudo-random) : seed를 이용하여 난수 생성하기 때문

random.seed(2)
random.random()
> 0.9560342718892494 # seed를 고정하였기 때문에 고정값만 출력

random.shuffle(a) # 해당 리스트의 순서를 무작위로 섞음
random.choice(a) # 해당 리스트에서 무작위로 하나를 선택
Random.sample(sequence, n) # 시퀀스에서 n만큼의 요소들을 랜덤으로 뽑아 리스트로 반환, 중복 x
```

## datetime
날짜/시간 모듈
```python
from datetime import datetime
datetime.now() # 현재 날짜와 시간을 지정된 형식으로 표시
datetime.today() # 현재 날짜와 시간을 지정된 형식으로 표시, .now()와 같음
datetime.utcnow() # 현재 날짜와 시간을 utc 시간 기준으로 표시

now = datetime.now()
now.strftime('%Y년 %m월 %d일 %a') # 날짜/시간을 원하는 형식으로 표시
now.year # 년 표시
now.day # 일 표시
now.weekday() # 요일을 0~6(월~일) 숫자로 표시
datetime(2023, 1, 1) # 데이터를 임의로 넣어서 설정 가능

from datetime import timedelta
timedelta(days=3) # 날짜/시간 변동 값 설정가능, 이용하여 +,-로 날짜계산 가능

new_year = datetime(2024, 1, 1)
now = datetime.now()

print(new_year - now)
> 81 days, 13:24:43.781133
```


