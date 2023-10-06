# 자료형
## 1. 변수
- 변수이름 = 값 : 값을 변수이름에 할당함
- 변수이름은 어떤 이름이든 상관없음 (영어, 숫자, `_`를 이용하여 선언)
- `False`, `def` 등과 같은 `keyword`는 사용불가

### 1.1 number
- 정수(`int`) : integer
- 부동 소수점(`float`) : floating point (32bit)
- 부동 소수점(`double`) : floating point (64bit)
- 복소수(`complex`) : complex
- Python에서는 자동으로 변수에 할당하는 자료형태에 따라 자동 형변환이 가능 (선언 x 가능)
### 1.2 Boolean
-  논리자료형(`bool`)
- `True == 1`, `False == 0`로 이루어진 자료형
### 1.3 None
- 데이터가 없음을 의미 (`NoneType`)
- 존재하지 않음, None != 0
### 1.4 String
- 문자열(`str`)
- `'`, `"`를 이용하여 표현
- `input()` 함수는 str 형으로 값을 받음
- `print()` 함수에서 str 출력관련
    - `print('str')`형태로 문자열을 출력할 수 있음 
        ex)    
        ```python
            print('\'안녕\'하세요?') # escape문 \(backslash)뒤의 문자를 문자 그대로 인식
            print('저는')
            print("'이도현'입니다.") #"를 이용해 str을 작성하면 강조를 위해 ' 사용가능
        ```
        - print('하나', '둘', '셋')
        - print('str', 변수, '둘') 과같이 이용가능하다
- 변수에 여러 줄의 문자열을 넣기위해서는 '''를 이용하여 작성할 수 있다.
```python
    a = '''
    여기는 문자열입니다.
    여러줄을 작성할 수 있습니다.
    '''
``` 
- \n : new line
- \t : tab
#### String interpolation
1. %-formating
    - `print('홍길동은 %s살입니다.' % age)`
2. str.format()
    - `print('홍길동은 {}살입니다.'.format(age)`
3. **f-string** (가장 최신이며 가독성 좋음. 주로 이용)
    - `print(f'홍길동은 {age}살입니다.')`

## 2. 연산자
### 2.1 산술연산자
- a + b : 덧셈
- a - b : 뺄셈
- a * b : 곱셈
- a / b : 나눗셈
- a ** b : 제곱 (a의 b승)
- a // b : a를 b로 나눈 몫
- a % b : a를 b로 나눈 나머지
> * mod 연산자
divmod(a,b) : a를 b로 나눈 `(몫, 나머지)` 출력

### 2.2 비교연산자
- 아래 연산의 결과를 `True`, `False`로 출력
    - a > b : a는 b 초과
    - a < b : a는 b 미만
    - a >= b : a는 b 이상
    - a <= b : a는 b 이하
    - a == b : a는 b와 같다
    - a != b : a는 b와 다르다
- 이때 각 변수는 숫자 뿐만이 아니라 문자열도 가능
### 2.3 논리연산자
- `and` : 양쪽 모두 `True`일 때, `True`를 반환
```python
print(True and True)
print(True and False)
print(False and True)
print(False and False)
```
> True    
> False    
> False    
> False

- `or` : 양쪽 모두 `False`일 때, `False`를 반환
```python
print(True or True)
print(True or False)
print(False or True)
print(False or False)
```
> True    
> True    
> True    
> False

- `not` : 값을 반대로 전환 
```python
print(not True)
```
> False
```python
a = False
print(not a)
```
> True

#### * 단축평가 (and / or)
```python
print(3 and 5) # True and True - 뒷 데이터가 중요
print(3 and 0) # True and False - 뒷 데이터가 중요
print(0 and 5) # False and True - 앞 데이터가 결정
print(0 and 0) # False and False - 앞 데이터가 결정
```
> 5    
> 0    
> 0    
> 0    
```python
print(3 or 5) # True or True - 앞 데이터가 True면 뒷 데이터 중요x
print(3 or 0) # True or False - 앞 데이터가 True면 뒷 데이터 중요x
print(0 or 5) # False or True  - 뒷 데이터가 중요해짐
print(0 or 0) # False or False - 뒷 데이터가 중요해짐
```
> 3    
> 3    
> 5    
> 0    
### 2.4 복합연산자
- 연산과 할당을 합쳐놓은 것으로 식을 간결하게 사용 가능
- 변수가 이전에 가졌던 값을 수정할당 하는 것등에 사용 가능
```python
a += b # a = a + b
a -= b # a = a - b
a *= b # a = a * b
a /= b # a = a / b
a //= b # a = a // b
a %= b # a = a % b
a **= b # a = a ** b
```
### 2.5 기타연산자
- concatenation
    ```python
    a = 'hi'
    b = 'hello'
    print(a + b) 
    ```
    > hihello
- containment
    ```python
    print('a' in 'apple')
    print('z' in 'apple')
    print(1 in [1, 2, 3])
    print(100 in [1, 2, 3])
    ```
    > True    
    > False    
    > True    
    > False
- Identity
    - is : 같은 메모리에 있는지 확인
    ```python
    a = 10
    b = 10
    c = 123123
    d = 123123
    e = [1, 2, 3]
    f = [1, 2, 3]
    print(a is b)
    print(a is not b)
    print(c is d)
    print(e is f)
    ```
    > True(-5 ~ 256의 값에 대해서는 같은 메모리 주소를 참조 (연산 빠르게))  
    > False   
    > False    
    > False

#### 연산자 우선순위
0. () 를 통해 그룹
1. **
2. 산술연산자(*, /)
3. 산술연산자(+. -)
4. 비교연산자(is, in)
5. 논리연산자(not)
6. 논리연산자(and, or)

## 3. 형변환
### 3.1 암시적 형변환(자동)
- 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환
```python
int_num = 3
float_num = 3.3
complex_num = 3 + 3j

print(int_num + float_num)
print(int_num + complex_num)
```
> 6.3 -> float    
> (6+3j) -> complex

### 3.2 명시적 형변환(의도)
- 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환
```python
a = '100'
print(int(a))
print(type(int(a)))
```
> 100    
> <class 'int'>

## 4. 시퀀스(sequence) 자료형
- 시퀀스는 데이터의 순서대로 나열된 자료구조
### 4.1 리스트(list)
- 선언 : 변수이름 = [value1, value2, value3]
- 접근 : 변수이름[index] #index = 0~

### 4.2 튜플(tuple)
- 선언 : 변수이름 = (value1, value2, value3)
- 접근 : 변수이름[index]
- list와 유사하지만 수정불가능(immutable)하다.
### 4.3 레인지(range)
- range(n) : 0부터 n-1까지 범위
- range(n, m) : n부터 m-1까지 범위
- range(n, m, s) : n부터 m-1까지 범위, +s만큼 증가하는 범위

### 4.4 문자열(string)
- 기본 데이터 구조 참고
### 4.5 시퀀스에서 사용가능한 연산/함수
```python
my_list = [1, 2, 3, 4, 5]
my_tuple = (11, 22, 33, 44, 55)
my_range = range(1, 10, 2)
my_string = '일이삼사오'
```
- indexing
```python
print(my_list[1])
print(my_tuple[1])
print(my_range[1])
print(my_string[1])
```
> 2    
> 22    
> 3    
> 이    
- slicing
```python
print(my_list[1:3])
print(my_tuple[1:3])
print(my_range[1:3])
print(my_string[1:3])

print(my_list[1:4:2])
print(my_range[2:7:2])

print(my_list[:3])
print(my_list[3:])
```
> [2, 3]    
> (22, 33)    
> range(3, 7, 2)    
> 이삼

> [2, 4]    
> range(5, 11, 4)      

> [1, 2, 3]    
> [4, 5]    

- in / not in
```python
print(11 in my_list)
print(11 in my_tuple)
print(1 in my_range)
print('일' in my_string)

print(11 not in my_list)
print(100 not in my_tuple)
print(1 not in my_range)
print('구' not in my_string)
```
> False    
> True    
> True    
> True    
>     
> True    
> True    
> False    
> True        

- concatenation
```python
print(my_list + [1, 2, 3, 4, 5])
print(my_tuple + (1, 2, 3))
```
> [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]    
> (11, 22, 33, 44, 55, 1, 2, 3)

- * 곱셈연산 : 시퀀스 반복
```python
print(my_string * 3)
print(my_list * 3)
print([0] * 10) # 리스트 초기화할 때
```
> 일이삼사오일이삼사오일이삼사오    
> [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5]    
> [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]


## 5. 시퀀스가 아닌 자료형

### 5.1 set
- 수학에서 사용하는 집합과 동일하게 처리(중복된 값이 없음)
- 선언 : 변수이름 = {value1, value2, value3}
### 5.2 dictionary
- 선언 : 변수이름 = {key1: value1, key2: value2, key3: value3}
- 접근 : 변수이름[key]
- dictionary는 key와 value가 쌍으로 이루어져있다.
- key에는 immutable한 모든 값을 사용가능. (불변값 : string, integer, ...)
- value에는 모든 데이터 가능. (list, dict도 가능)
