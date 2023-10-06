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

### 조건표현식
- if/else 조건문을 한줄 표현식으로 나타내는 방법
```python
true_value if <조건식> else false_value
```
ex)
```python
if 1 < 0:
    print('True')
else:
    print('False')
# True
######################################
print('True') if 1 < 0 else print('False')    
# True
```

## 반복문

### while문
- while문은 <조건식>이 참인 경우 내부 수행을 반복 진행, 거짓인 경우 while문을 빠져나감
```python
while <조건식>:
    실행할 코드
```

### for문
- 정해진 범위 내의 반복
- sequence 자료형인 list, tuple, range, string을 이용가능
```python
for variable in sequence:
    실행할 코드
```
```python
numbers = [1, 2, 3, 4, 5]
# list: number라는 변수를 만들어 numbers의 각 값을 할당하여 사용
for number in numbers:
    print(numbers[number:])
# range
for i in range(5):
    print(i)
# tuple
for i in (1, 2, 3, 4, 5):
    print(i)
# string
word = input('단어를 입력해주세요: ')
for char in word:
    print(char)
```

#### dictionary 반복
 1. for key in dict:
    - 기본적으로 dictionary의 key 값을 사용가능
 2. for key in dict.keys():
    - `.keys()`를 이용하여 dictionary의 `key 리스트`를 시퀀스로 사용가능
 3. for value in dict.values():
    - `.values()`를 이용하여 dictionary의 `value 리스트`를 시퀀스로 사용가능
 4. for key, value in dict.items():
    - `items()`로 (key, value)를 한번에 사용 가능

### break
- 반복문을 종료시킴
- for문 내부에 if문을 이용해 어떤 조건에서 종료, if문 안에 있지만, 가까운 for문을 종료
- while에서도 동일하게 사용가능
```python
for i in range(100):
    print(i)
    if i > 10: 
        print('10넘었어!!')
        break

# 0
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
# 10
# 11
# 10넘었어!!
```
### continue
- continue 이후의 코드를 실행하지 않고 다음 반복문을 실행
```python
for i in range(10):
    if i % 2:
        continue    
    print(i)

# 0
# 2
# 4
# 6
# 8
```
### else
- else문은 끝까지 반복이 진행이 된 후 실행 (break를 만나지 않은 경우)
```python
numbers = [1, 2, 3, 4, 5]
target = 5

# numbers를 반복하다 target이 있으면 True, 없으면 False출력

for number in numbers:
    if number == target:
        print(True)
        break
else:
    print(False)
# True
```
### pass
- for/if 문 작성시, 코드는 필요하지만, 아무 작업도하지 않기를 원할 때 사용된다. 나중에 코드를 추가 할 계획이거나 , 예외가 발생했을 때 처리
### match
- C/C++의 switch, case와 유사
- 객체를 받아서 하나 이상의 매칭 패턴을 기준으로 테스트하고 매칭되는 항목을 찾으면 동작 수행
```python
match value:
    case 조건:
        실행할 코드
    case 조건:
        실행할 코드
    case _:
        실행할 코드
```