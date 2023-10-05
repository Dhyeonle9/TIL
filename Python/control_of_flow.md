# 제어 흐름

## 1. 조건문 if

```python
if <조건식>:
    if의 조건식이 참인 경우 실행하는 코드
else:
    if의 조건식이 거짓인 경우 실행하는 코드
```

1. `if` 문은 반드시 참/거짓을 판단할 수 있는 `조건식`과 함께 사용한다.
2. `조건식` 이 참인 경우 `:` 이후의 문장을 실행한다.
3. `조건식` 이 거짓인 경우 : `else:` 이후의 문장을 실행한다.

ex) 
값을 입력받아 **12/25** 일 때 '크리스마스입니다. ' 출력
아닐 때 '크리스마스가 아닙니다.' 출력
```python
my_string = input()

if my_string == '12/25':
    print('크리스마스입니다.')
else:
    print('크리스마스가 아닙니다.')
```

ex)
값을 입력받아 짝수일 때 '짝수입니다.'
             홀수일 때 '홀수입니다.' 출력
```python
num = input('숫자를 입력해주세요 : ')
num = int(num)

if num % 2 == 1:
    print('홀수입니다.')
else:
    print('짝수입니다.')
```
```python
# num을 2로 나눈 나머지는 0, 1 두가지 경우가 있다.
# if 조건식에 0, 1는 자동 형변환이 일어나 False/True로 변환된다.

num = input('숫자를 입력해주세요 : ')
num = int(num)

if num % 2: # 2로 나눈 나머지 == 1 == True (1)
    print('홀수입니다.')
else:
    print('짝수입니다.')
```
### elif
```python
if <조건식>:
    if 조건이 참인 경우 실행
elif <조건식>:
    elif 조건이 참인 경우 실행
...
else:
    위의 조건식에 하나도 부합하지 않는 경우 실행
```
ex)
```python
score = int(input('점수를 입력해주세요: '))

# 90점이상 A (95점이상이라면 good 추가)
# 80점이상 B
# 70점이상 C
# 나머지 F
if 0<=score<=100:
    
    if score>=90:
        print('A')
        if score>=95:
            print('good')
    elif score>=80:
        print('B')
    elif score>=70:
        print('C')
    else:
        print('F')
else:
    print('잘못된 값입니다.')
```