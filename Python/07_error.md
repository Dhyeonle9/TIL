# Error
## SyntaxError
- 파이썬 문법 오류가 발생하는 경우 발생
- 예외처리 안됨
```python
if True:
    pass
else

# else
#       ^
#   SyntaxError: expected ':'
```

## ValueError
- 부적절한 값을 가진 인자를 받았을 때 발생
- 참조값이 없을 때 발생
```python
int('4.5')

# ---->int('4.5')
# ValueError: invalid literal for int() with base 10: '4.5'
```
## IndexError
- 인덱스 범위를 벗어나는 경우 발생하는 에러
```python
a = [1, 2, 3, 4, 5]
a[10]

# IndexError: list index out of range
```
## NameError
- 지역변수, 전역 변수 이름을 찾을 수 없는 경우에 NameError가 발생
- 변수를 선언하지 않고 사용할 때
```python
a = 1
b = 2
print(c)

# NameError: name 'c' is not defined
```
## TypeError
- 잘못된 타입을 전달했을 때 발생하는 에러
- 기대하지않은 타입의 변수가 입력되었거나, 함수 호출 시 형식에 맞지 않은 경우
```python
1 + '1'

# TypeError: unsupported operand type(s) for +: 'int' and 'str'

random.sample([1, 2, 3, 4], 2, 2, 2, 2)

# TypeError: Random.sample() takes 3 positional arguments but 6 were given
```
## ZeroDivisionError
- 0으로 나누려는 경우에 발생하는 에러
```python
a = 9 / 0
print(a)

# ZeroDivisionError: division by zero
```

## ModuleNotFoundError (FileNotFoundError)
- 모듈/파일에 접근하려 할 때, 해당 모듈/파일이 없는 경우 발생하는 에러
```python
f = open("blockdmask.py", "r")

# FileNotFoundError: No such file of directory: 'blockmask.py'
```
## KeyError
- 딕셔너리에서 접근하려는 키 값이 없을 때 발생하는 에러

## OverflowError
- 연산의 결과가 너무 커서 데이터 타입이 표현할 수 있는 숫자의 범위를 넘어가는 경우 발생하는 에러
```python
a = 2 ** 123456
b = 5
print(a/b)

# OverflowError: integer division result too large for a float
```
## AttributeError
- 어트리뷰트 참조나 대입이 실패한 경우에 발생하는 에러
- 클래스(모듈)의 객체에 해당하는 메서드나 속성을 잘못 호출하거나 대입했을 때 발생하는 에러
 ```python
 import math

# 정상 접근
a = math.ceil(1.2)
print(a)

# math ceil2 라는 메서드는 없습니다.
b = math.ceil2(1.2)
print(b)

# AttributeError: module 'math' has no attribute 'ceil2'
 ```

# 예외처리
    ```python
    try:
        code
    except 에러종류:
        code
    ```
 - 에러가 발생하면 프로그램이 비정상 종료됨
 - 에러가 발생했을 때 프로그램이 죽지 않도록 하는 것이 예외처리
 - `try`, `except`, `else`, `finally`를 이용하여 처리됨

 - 사용법
    - try, except 예외처리
        ```python
        try:
            my_list = [1, 2, 3]
            print(my_list[100])
        except IndexError as err: # 에러에 해당하는 상세 내용을 가져올 수 있음
            print('범위에 문제가 있습니다.')
            print(err)
        
        # 범위에 문제가 있습니다.
        # list index out of range
        ```
    - else: 에러가 발생하지 않았을 때 거치는 구문. try, except와 함께 사용해야함
        ```python
        try:
            numbers = [1, 2, 3]
            num = numbers[1]
        except:
            print('오류발생')
        else:
            print(num **3)

        # 4
        ```
    - finally: 에러 발생과 무관하게 무조건 거치는 구문.
        ```python
        try:
            numbers = [1, 2, 3]
            num = numbers[10]
        except:
            print('오류발생')
        finally:
            print('end')
        
        # 오류발생
        # end
        ```
    - raise: 예외를 강제로 발생시키는 상황에서 사용
        ```python
            for i in range(100):
        if i == 50:
            print(i)
            raise

        # 50
        # RuntimeError: No active exception to reraise
        ```
- 연습
```python
def my_div(num1, num2):
    result = 0
    try:
        result = num1 / num2
        print(f'{num1} 나누기 {num2}는 {result}입니다.')

    except ValueError as error1:
        print('ValueError 입니다.')

    except TypeError as error2:
        print('TypeError입니다.')

    except ZeroDivisionError as error3:
        print('0으로 나눌 수 없습니다.')

    else:
        return result
    finally:
        print('end')

print(my_div(5, 0))
print(my_div('5', '0'))
print(my_div(5, 2))

# 0으로 나눌 수 없습니다.
# end
# None
# TypeError입니다.
# end
# None
# 5 나누기 2는 2.5입니다.
# end
# 2.5
```
- 일반적으로는 예외의 경우 return None(기본값)으로 하고, else의 경우 원하는 값을 return하는 식으로 이용