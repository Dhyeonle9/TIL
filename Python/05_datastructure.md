# 메소드
- 함수(Function) : 함수는 특정 작업을 수행하는 "코드조각"으로  전역, 지역이던 "독립된 기능"을 수행하는 단위
- 메소드(Method) : 클래스, 구조체, 열거형 등 객체에 포함되어있는 "함수"를 메소드라고 함(다른말로 "클래스 함수")

## 문자열 메소드
- `.capitalize()` : 문자열의 첫글자를 대문자로 바꿈
- `.title()`: 문자열에서 단어의 첫글자를 모두 대문자로 바꿈
- `.upper()`: 문자열의 모든 글자를 대문자로 바꿈
- `.join()`: 매개변수로 들어온 리스트 요소들을 합쳐서 하나의 문자열로 바꾸어 반환
    ```python
    ''.join(리스트)
    ```
- `.strip([chars])`: 문자열 좌우의 공백 혹은 원하는 문자열을 제거해준다.
    ```python
    string.strip()
    string.strip('char')
    #char에 따라 원치않게 더 지워질 수도 있다. 예를들면 'hi'라는 문자열을 strip하려고 하면, h와 i를 순서대로 제거한다
    ```
- `.find(x)`: 문자열 앞에서부터 x를 찾아 위치를 표시해준다. (가장 앞의 하나만 표시하고 없을시 **-1** return)
- `.index`: 문자열 앞에서부터 x를 찾아 위치를 표시해준다. (가장 앞의 하나만 표시하고 없을 시 **error**)
- `.split(x)`: 공백 혹은 'x'를 기준으로 문자열을 쪼개고 리스트로 반환한다.
    ```python
    a.split() # 공백을 기준으로
    a.split('_') # '_'를 기준으로
    ```
- `.count(x)`:문자열에서 해당 문자를 포함하는 수를 출력
    ```pyhon
    'wooow'.count('o') 
    # 7
    ```

## 리스트 메소드
- `.append(x)`: 리스트의 끝에 새로운 요소를 추가
- `.extend(iterable)`: 반복가능한 객체를 넣으면, 리스트에 더해줌
    ```python
    numbers = [1, 5, 2, 6, 2, 1]
    a = [99, 100]
    numbers.extend(a)
    print(numbers)
    # [1, 5, 2, 6, 2, 1, 99, 100]
    # print (numbers + a)와 같다
    ```
- `.insert(idx[, x])`: 원하는 위치(idx) 앞에 x라는 값을 추가해 줌, idx에 음수를 입력하면 배열의 끝을 기준으로 처리 (x는 객체로 추가됨)
### append/extend/insert의 차이
1) append 함수

    arry.append(x) 형태로 사용한다. x를 arry의 맨 끝에 객체로 추가다. x가 iterable 자료형이더라도 전체를 하나의 객체로 해서 요소로 추가한다.

2) extend 함수

    array.extend(iterable) 형태로 사용한다. iterable의 각 요소를 하나씩 array의 끝에 요소로 추가한다. append 함수와 다른 점은 괄호 안에 iterable 자료형만 올 수 있다.

3) insert 함수

    array.insert(i, x) 형태로 사용한다. 원하는 위치 i에 x를 삽입할 수 있다. 값 x는 객체로 추가된다. append 함수와 마찬가지로 iterable 자료형이더라도 하나의 요소로 삽입된다.
- `.remove(x)`: 원하는 값을 리스트에서 지울때 사용 좌측에서 부터 처음만난 x만 삭제, 없을때는 error 발생
- `.pop(idx)`: 가장 뒤에 있는 값 혹은 idx의 값 하나 return 후 삭제, 해당 idx 없을때는 index error 발생
- `.del(idx)`: idx에 해당하는 값을 삭제, 제거한 값 return하지 않음
- `.sort()`: 리스트의 요소를 순서대로 정렬, 원본을 바꾸고 `return None`
    ```python
    numbers = [2, 3, 1]
    print(numbers.sort())
    print(numbers)

    numbers.sort(reverse=True)
    print(numbers)
    # None
    # [1, 2, 3]
    # [3, 2, 1]

    #sorted(numbers)는 함수, 원본을 바꾸지 않고 정렬값을 return
    ```
- `.reverse()`: 리스트 값들을 idx를 뒤집어 출력(numbers[ : : -1]와 같음)

### list copy
```python
origin_list = [1, 2, 3] 
copy_list = origin_list # 기존 객체를 재할당 (call by reference)
copy_list[0] = 100
print(origin_list)
print(copy_list)
# [100, 2, 3]
# [100, 2, 3]
# 두 객체는 값을 같은 주소에서 가져옴
a = [1, 2, 3]
b = list(a) # 새로운 리스트를 만듬, 복사하고 싶다면 이렇게
# b = a[:] 도 가능
```
> depth가 있는 리스트들의 경우, deepcopy() 이용해야함
```python
import copy

a = [1, 2, [99, 100]]
b = copy.deepcopy(a) # 리스트안에 또 다른 리스트들이 있을 때 복사하여 개별적으로 이용하려면 .deepcopy 이용

b[2][1] = 1000

print(a)
print(b)
```

### list comprehension
참고[]
List Comprehension은 대괄호 사이에 for문, 조건문 등을 사용하여 간결하게 List를 만들 수 있게 해줌
1. 기본구조: 표현식 + for문 
    ```python
    result = [표현식 for 변수 in list]
    ```
2. 표현식 + for문 + 조건문
    ```python
    result = [표현식 for 변수 in 리스트 if 조건문]
    ```
3. 조건문 + for문
    ```python
    result = [표현식 if 조건문 else 표현식 for 변수 in 리스트]
    ```
4. 중첩 for문
    ```python
    result = [표현문 for 변수1 in 리스트1 for 변수2 in 리스트2 ...]
    ```

## 딕셔너리 메소드
- `.pop(key[, default])`: 지정된 key에 해당하는 item 제거 후, 제거된 item value를 return.
> 해당하는 key가 없을때 default value가 없다면 에러 발생, 있다면 default value 반환
- `.update(key= value)`: key에 해당하는 value 수정, 해당하는 key가 없다면 추가
- `.get(key[, default])`: key에 해당하는 value를 받아옴. key가 없다면 None 반환

### dict comprehension
```python
result = key: value for 반복문 in iterable
```

## 세트 메소드
- `.add(x)`: 입력된 객체를 순서없이 추가, 같은값 추가x
- `.update(x)`: 입력된 객체(sequence)를 쪼개어서 순서없이 추가, 같은값 추가x
```python
words = {'apple', 'banana', 'carrot'}
words.update('orange')
print(words)
# {'g', 'banana', 'r', 'carrot', 'o', 'n', 'apple', 'a', 'e'}
# 데이터 그대로 추가하고 싶다면 {'orange', 'grape'}처럼 set를 update 해야함
```
- `.remove(x)`: 해당하는 요소를 지움, 해당 요소가 없다면 error 발생
- `.discard(x)`: 해당하는 요소를 지움, 해당 요소가 없어도 오류발생하지 않음
- `.pop()`: 요소를 랜덤으로 제거하고 제거된 요소를 반환

## 기타 함수
- `map(function, iterable)`: 두 번째 인자로 들어온 반복 가능한 자료형 (리스트나 튜플)을 첫 번째 인자로 들어온 함수에 하나씩 집어넣어서 함수를 수행하는 함수
(반복)
    - map 함수의 반환 값은 `map 객체`이기 때문에 자료형을 list 혹은 tuple로 형변환시켜줘야 함
    
- `filter(function, iterable)`: 특정 조건으로 걸러진 요소들을 iterable한 객체로 return 해줌
    - filter에 들어가는 function은 T/F를 반환해야 함
    ```python
    def is_odd(x):
        if x % 2 == 1:
            return True
        else:
            return False

        # return bool(x % 2)

    numbers = [1, 2, 3, 4, 5]

    # for문
    # result = []

    # for number in numbers:
    # if is_odd(number):
    #     result.append(number)
    # print(result)

    result2 = filter(is_odd, numbers)
    print(list(result2))
    # [1, 3, 5]
    ```

- `zip`
    - 두개의 리스트를 쌍으로 사용할때 이용
    - 갯수가 맞아야함
    - 같은 인덱스의 리스트 값들을 튜플로 내어줌
    - lazy한 함수로 zip 객체로 값을 return하기 때문에 list 혹은 tuple로 형변환 필요함
```python
a = [1, 2, 3]
b = [100, 200, 300]

result = zip(a, b)
print(result)
print(list(result))

# <zip object at 0x00000278AABAA2C0>
# [(1, 100), (2, 200), (3, 300)]
```
