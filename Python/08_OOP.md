# OOP(Object-Oriented Programming:객체 지향 프로그래밍)
객체 지향 프로그래밍은 여러 객체들의 상호작용으로 프로그램 로직을 구성하는 프로그래밍 패러다임
![OOP](./assets/OOP.png)
    

## OOP의 특징
1. 캡슐화, Encapsulation
    - 특정한 목적을 가진 데이터와 메소드를 클래스 하나로 묶는것
    - 객체 내부에서 필요로 하는 정보를 은닉하는 특징이 있음
    - 데이터는 외부에서 직접 접근하면 안되고 함수를 통해서만 접근해야 함
2. 상속, Inheritance
    - 이미 정의되어있는 상위 클래스와 메소드 등의 속성을 하위 클래스가 물려받음
    - 코드 중복을 막을 수 있어 코드가 더 간단해짐 (유지보수 간단)
3. 추상화, Abstraction
    - 불필요한 정보는 숨기고 중요한 정보만을 표현해 프로그램을 간단히 만듬
4. 다형성, Polymorphism
    - 형태가 같은데 다른 기능을 함
    - 부모 클래스로 부터 상속 받은 속성을 자식 클래스에서 재정의 할 수 있음(오버라이딩- 같은 이름의 메소드가 여러 클래스에서 다른 기능을 하는 것)

## OOP의 장/단점
1. 장점
    - 코드 재사용이 용이
    - 유지보수가 쉬움
    - 대형 프로젝트 용이(기능을 클래스 단위로 모듈화시켜 개발가능)

2. 단점
    - 처리속도가 상대적으로 느릴 수 있음
    - 객체가 많으면 불필요한 용량이 커질 수 있음
    - 설계시 시간이 많이 필요

## 용어 정의
1) `객체(object)`: 속성(attribute)과 행위(method)을 가진 데이터(숫자, 문자, 함수 등 모든 것) (구현할 대상)
2) `클래스(class)`: 같은 종류의 집단에 속하는 속성(attribute)과 행위(method)를 정의한 것 (객체를 생성하기 위한 설계도)
3) `인스턴스(instance)`: 클래스를 실제 메모리상에 할당 한 것 (소프트웨어 상 구현된 실체)
4) `속성(attribute)`: 클래스/인스턴스가 가지고 있는 데이터/값 `인스턴스.속성`으로 이용
    ```python
    num = 1 + 1j
    type(number) # complex

    print(number.real)
    print(number.imag)

    ```
5) `행위(method)`: 클래스/인스턴스가 가지고 있는 함수/기능 `인스턴스.함수()`로 이용
    ```python
    my_list = [1, 2, 3, 4]
    print(type(my_list)) # class 'list'>
    my_list.reverse()
    print(my_list)
    ```
## Class
- 클래스 선언
    ``` python
    class ClassName:
        attribute = value

        def method_name(self):
            code
    ```
- 인스턴스화
    ```python
    ClassName()
    ```

#### 예시1
```python
# 선언
class MyClass:
    name = 'kim'

    def hello(self):
        return 'hello'

# 인스턴스화
a = MyClass() # 인스턴스 a에 클래스 할당


print(a.name) # MyClass라는 클래스의 인스턴스 a의  attribute에 접근
print(a.hello()) # 인스턴스 a의 method에 접근

b = MyClass() # 인스턴스 b에 클래스 할당

b.name = 'park' # 인스턴스의 속성에 데이터 입력
print(b.name) 
print(b.hello()) 
```

#### 예시2
```python
class Phone:
    power = False
    number = '010-0000-0000'
    book = {}
    model = ''

    def on(self): # self: 인스턴스 자기자신
        if self.power == False:
            self.power = True
    
    def off(self):
        if self.power == True:
            self.power = False

    def call(self, target):
        if self.power == True:
            print(f'제 번호는 {self.number}입니다.')
            print(f'{target}로 전화 거는 중')
        else:
            print('핸드폰을 켜주세요')

my_phone = Phone()
my_phone.number = '010-1234-1234'
print(my_phone.number)
# 010-1234-1234

your_phone = Phone()
print(your_phone.number)
# 010-0000-0000

my_phone.on() # => my_phone.on(my_phone)
print(my_phone.power)
print(your_phone.power)
my_phone.off()
print(my_phone.power)
# True
# False
# False

my_phone.on()
my_phone.call('112')
your_phone.on()
your_phone.call('119')

# 제 번호는 010-1234-1234입니다.
# 112로 전화 거는 중
# 제 번호는 010-0000-0000입니다.
# 119로 전화 거는 중
```

#### 연습 : MyList라는 클래스에 append 함수, pop 함수와 같은 메소드 구현

```python
class MyList:
    data = []

    def append(self, add):
        self.data += [add]
        # add를 list 로 받아올 수도 있다면 아래와 같이 구현 가능
        # if isinstance(add, list):
        #     self.data += add
        # else:
        #     self.data += [add]
    def pop(self):
        p_data = self.data[-1]
        del self.data[-1]
        return p_data
```

## 생성자, 소멸자
```python
class MyClass:

    def __init__(self): # 인스턴스화 과정에서 자동으로 실행
        pass

    def __del__(self):
        pass
```
#### 예시
```python
class Person:
    name = 'noname'

    def __init__(self, name='익명'):
        self.name = name
        print('생성됨')
        
    def __del__(self):
        print('소멸됨')


p1 = Person('kim') # => Person.__init__('Kim')
print(p1)
print(p1.name)

p2 = Person('park')
print(p2.name)

p3 = Person()
print(p3.name)

print(Person.name)

p1.phone = '010-1234-1234'
print(p1.phone)

# 생성됨
# <__main__.Person object at 0x000001C1B88F0F10>
# kim
# 생성됨
# park
# 생성됨
# 익명
# noname
# 010-1234-1234

del p1
# p1 인스턴스 삭제
```

### 클래스변수
- 클래스 선언 블록 최상단에 위치
### 인스턴스변수
- 인스턴스 내부에서 생성한 변수(= self.variable)
```python
class MyClass:
    class_variable = '클래스변수'

    def __init__(self, name):
        self.instance_variable = '인스턴스변수'
```
예시
```python
class Person:
    name = '홍길동' # => 클래스변수
    phone = '010-1234-1234'

    def __init__(self, name):
        self.name = name # => 인스턴스변수
```

### 클래스 메소드, 인스턴스 메소드, 스태틱 메소드
```python
class MyClass: 
    def instance_method(self): # 인스턴스 메소드
        pass

    @classmethod
    def class_method(cls): # 클래스 메소드
        pass

    @staticmethod
    def static_method(): # 스테틱 메소드
        pass
```
1. `인스턴스 메소드`: 가장 흔히 쓰이는 것으로 인스턴스 변수에 엑세스할 수 있도록 첫번째 인자에 항상 객체 자신을 의미하는 `self`를 가짐
    - 메소드를 호출한 객체에만 영향을 미침
    - 객체 속성에 접근 가능
    - 클래스 안에서는 `self.메소드`, 밖에서는 `객체.메소드`로 호출

2. `클래스 메소드`: 인스턴스 없이 호출이 가능하고, self 파라미터 대신 클래스를 의미하는 `cls`를 인자로 가짐
    - 클래스 자체에서 직접 호출
    -  객체의 속성/메소드에 직접적으로 엑세스는 불가능하고 `cls.클래스 속성`으로 클래스 속성에는 접근가능
    - `클래스.클래스메소드` 혹은 `객체.클래스메소드`로 호출

3. `스태틱 메소드`: 객체와 독립적이지만, 로직상 클래스 내에 포함되는 메소드, self 파라미터를 가지고 있지않아 인스턴스 변수에 접근 불가능하다. 
    - 정적 메소드 내부에서 `클래스.클래스 속성`으로 클래스 속성에는 접근 가능
    - 메소드 실행이 외부 상태에 영향을 끼치지 않는 순수함수를 만들 때 사용(인스턴스 상태를 변화시키지 않는 메소드)
    - `클래스.정적메소드`혹은`객체.정적메소드`로 호출 가능(전자를 주로 이용)
예시
```python
class Puppy:
    num_of_puppy = 0

    def __init__(self, name): # 인스턴스 안의 메소드가 필요할 때
        self.name = name
        Puppy.num_of_puppy += 1

    @classmethod # => decorator:
    def get_status(cls): # 클래스 안의 메소드가 필요할때
        print(f'현재 강아지는 {cls.num_of_puppy}마리입니다.')

    @staticmethod
    def bark(msg): # 아무 정보도 필요 없을때
        return msg

    def bark2(self, msg):
        return f'{self.name}은 {msg}합니다.'

p1 = Puppy('인절미')
p2 = Puppy('백구')
p3 = Puppy('흰둥이')

print(Puppy.num_of_puppy)
print(p1.num_of_puppy)

Puppy.get_status()
p1.get_status()

print(p1.bark('멍멍'))
print(p2.bark('그르릉'))

print(p1.bark2('멍멍'))

# 3
# 3
# 현재 강아지는 3마리입니다.
# 현재 강아지는 3마리입니다.
# 멍멍
# 그르릉
# 인절미은 멍멍합니다.
```

## 상속
```python
class ParentClass:
    속성
    def 메소드:

class ChildClass(ParentClass):
    속성
    def 메소드

```
- 클래스에서 상속이란, 물려주는 클래스(Parent Class, Super class)의 내용(속성과 메소드)을 물려받는 클래스(Child class, sub class)가 가지게 되는 것
- 자식클래스를 선언할때 소괄호로 부모클래스를 포함
- 자식클래스에서는 부모클래스의 속성과 메소드는 기재하지 않아도 포함

예시
```python
class Person: # 부모클래스
    def __init__(self, name, email, phone, location):
        self.name = name
        self.email = email
        self.phone = phone
        self.location = location

class Student(Person): # 자식클래스1
    def __init__(self, student_id):
        self.name = name
        self.email = email
        self.phone = phone
        self.location = location
        self.student_id = student_id

class Soldier(Person): # 자식클래스2
    def __init__(self, name, email, phone, location, soldier_id):
        # super() => Person (부모클래스)의 생성 메소드를 실행, 부모클래스의 인스턴스 속성과 동일한 속성 생성
        super().__init__(name, email, phone, location) 
        self.soldier_id = soldier_id
```

### 다중상속
자식 클래스는 여러개의 부모클래스를 상속받아 사용할 수 있음

예시
```python
class Person:
    def __init__(self, name):
        self.name = name

    def breath(self):
        print('후하')

class Mom(Person):
    gene = 'xx'

    def swim(self):
        print('어푸어푸')

class Dad(Person):
    gene = 'xy'

    def run(self):
        print('다다다')

class Baby(Mom, Dad):
    pass

##########################
b = Baby('금쪽이') 
print(b.name)
print(b.gene) # 중복으로 가지고 있을 때 상속받은 클래스의 가장 앞부터

b.swim()
b.run()
b.breath()

# 금쪽이
# xx
# 어푸어푸
# 다다다
# 후하
```

