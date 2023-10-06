# 함수
- 입력값을 가지고 어떤 일을 수행한 후 그 결과물을 내어놓는 것
- 반복된 연산을 편리하게 하기위해 사용
![함수](/Review/assets/function.png)

## 함수의 선언과 호출
- 함수의 선언
    ```python
        def func_name(parameter1, parameter2):
            code1
            code2
            ...
            return value
    ```
- 함수의 호출
    ```python
    func_name(para1, para2)
    ```
## 함수의 return
    - 함수가 return을 만나면 해당 값을 반환하고 함수를 종료
    만약 return이 없다면 None을 자동으로 반환
    return은 오직 `하나의 객체`만 반환
    ```python
    def my_list_max(list1, list2):
        if sum(list1) > sum(list2):
            return list1
        else:
            return list2

    my_list_max([1, 2, 3], [2, 3, 4])
    # [2, 3, 4]
    ```
## 함수의 인수
- 매개변수(parameter): 함수에 입력으로 전달된 값을 받는 변수
- 인수(arguments): 전달인자, 함수 호출시 실제로 값을 가져오늘 input의 값
### 위치인수
- 기본적으로 함수는 인수의 위치로 판단
    ```python
    # 원기둥 부피
    def cylinder(r,h):
        return 3.14 * r**2 * h

    cylinder(10, 5)
    # 785.0
    ```
    위에서 함수 `cylinder(10, 5)` 호출시 
인수는 차례대로 r = 10, h = 5로 입력
### 기본값(기본 인수)
    ```python
    def func(p1=v1):
        code...
        return p1
    ```
- 매개변수에 기본값을 설정해두고 호출 시 입력하는 값이 없어도 설정한 값으로 계산하도록 하는 인수
- 기본값을 가지는 인수는 기본값이 없는 인수 뒤에 채움, 그렇지 않으면 오류발생
    ```python
    def greeting(age, name='익명'):
        return f'{name}님은 {age}살입니다.'

    print(greeting(50, '홍길동'))
    print(greeting(50))

    # 홍길동님은 50살입니다.
    # 익명님은 50살입니다.
    ```
### 키워드 인자
- 함수 호출시 내가 원하는 위치에 직접적으로 특정인자 전달 가능
    ```python
    def greeting(age, name='익명'):
        return f'{name}님은 {age}살입니다.'

    print(greeting(10))
    print(greeting(20, '홍길동'))
    print(greeting(name='홍길동', age=30))

    # 익명님은 10살입니다.
    # 홍길동님은 20살입니다.
    # 홍길동님은 30살입니다.
    ```
### 가변인자리스트
    ```python
    def func(*parms):
        code
    ```

- 함수의 매개변수 숫자를 모를때 사용하는 방식
- 매개변수 앞에 `*`를 붙여주면 입력되는 인수 갯수와 상관없이 함수내에서 튜플로 인식

    ```python
    def my_print(*words):
        print(words)
        print(type(words))

    my_print('a', 'b', 'c')

    # ('a', 'b', 'c')
    # <class  'tuple'>

    ```
### 정의되지않은 키워드 인자 처리하기
    ```python
    def func(**kwargs):
        code
        ...
    ```
- 정해지지않은 키워드 인자(a='1' 형태)를 이용하여 함수를 호출할 때
- 매개변수 앞에 `**`를 붙여줌.
- `**kwargs`는 {key: value}와 같은 dictionary 형식으로 전달됨
    ```python
    def fake_dict(**kwargs):
        for key, value in kwargs.items():
            print(f'{key}는 {value}입니다.')

    fake_dict(a='10', b='20')
    fake_dict(korean='안녕', english='hello') 
        
    # a는 10입니다.
    # b는 20입니다.
    # korean는 안녕입니다.
    # english는 hello입니다.
    ```
### dictionary를 인자로 넣기(unpacking)
- 여러개의 인수(여기서는 키워드 인수)를 입력해야하는 함수에서, 딕셔너리 앞에 `**`를 붙여주면 각각의 인수를 풀어서 넣을 필요가 없음
- 함수의 매개변수와 딕셔너리의 key값이 같아야함
    ```python
    def sign_up(id, pw, pw_confirmation):
        if pw == pw_confirmation:
            print(f'{id}님 회원가입이 완료되었습니다.')
        else:
            print(f'비밀번호가 일치하지 않습니다.')

    # sign_up('dohyeon', '1234', '1234')는 아래와 같음
    account = {
        'id': 'dohyeon',
        'pw': '1234',
        'pw_confirmation': '1234',
    }
    sign_up(**account)
    ```
### lambda 표현식
    ```python
    lambda parameter: expression
    ```
- 익명함수라고도 부르며, 식형태로 간편하게 작성할 수 있어서 다른 함수의 인수로 함수를 넣을 때 주로 사용 (혹은 단순 코드 간결작성시)
- 람다함수 내부에서 변수를 생성할 수 없고, 반환부를 제외한 다른 로직 삽입할 수 없음
- 재사용 권장하지 x (일회용)

### 타입힌트
- 함수의 input/output 인자들의 형태를 알려주기 위한 힌트
- 동작에 방해되지않음
    ```python
    def my_sum(a: int, b: int) -> int:
    return a + b
    ```
### 이름공간
python에서 사용되는 이름들은 이름공간(namespace)에 저장되어있습니다.
- Local scope: 정의된 함수 내부 (가장 가까운 곳)
- Enclosed scope: 상위 함수
- Global scope: 전역, 함수 밖의 변수 혹은 import된 모듈
- Built-in scope: python이 기본적으로 가지고 있는 함수 혹은 변수
> 함수에서의 우선순위는 지역변수 > 외부 함수의 지역변수 > 전역변수 > 내장형
### 재귀함수(recursive)
- 재귀함수는 함수 내부에서 자기 자신을 호출하는 함수
- 자신의 로직을 내부적으로 반복하다가, 일정한 조건이 되면 함수 이탈 return
- ex) factorial, Fibonacci numbers
- 장점: 변수를 여러개 만들 필요 없음
        반복문 사용하지않아도 되어 코드 간결
- 단점: 지속적으로 함수 호출하게 되어, 메모리 많이 사용 -> 속도 저하
        함수 호출 -> 복귀 위한 컨텍스트 스위치 비용 발생
```python
# 팩토리얼
def fact(n):
    result = 1
    while n > 1:
        result *= n
        n -= 1

    return result
```
의 반복문 형태를 재귀함수로 아래와 같이 표현 가능
```python
def factorial(n):
    if n <= 1:
        return 1
    else:
        return factorial(n-1) * n
```