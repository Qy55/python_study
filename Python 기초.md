# Variable Types and Operator
## Boolean Type
```python
var_for_true = True
var_for_false = False
```
- 참과 거짓을 나타내기 위해 사용
- `True`, `False`를 사용해 표시(대소문자 구분 주의)

## Numeric Type
```python
# 정수형
a = 1
## 2, 8, 16진법
base_bin = 0b0101
base_oct = 0o64
base_hex = 0x8b

# 실수형
a = 0.1
## 지수 표현
hat_large = 2.4E5
hat_small = 2.4e5
hat_negative = 4.23e-8
```
- 정수와 실수를 나타낼 때 사용
- 2, 8, 16진법의 수를 입력할 땐 각각 `0b`, `0o`, `0x`를 앞에 붙여 표현하면 해당 진법의 수를 저장
	- 어떤 진법으로 저장하든 `print()` 를 통해 변수를 출력하는 경우 10진법으로 출력하는 것이 Default
	- 변수를 2, 8, 16 진법으로 변환해 출력하고 싶다면 `bin()`,`oct()`, `hex()`를 사용하면 해당 진법의 문자열로 반환
	- 각 진법의 수로 사용될 수 없는 경우(ex. 8진법으로 표현되었으나 8 이상의 숫자가 사용) 에러 발생
- 부동 소수점 표현은 지수 표현 문자인 `E`, `e`를 사용해 표현 할 수 있으며, 이 때  지수 표현 문자 뒤에 10의 지수를 적어 사용하며, 10의 지수로는 음수 또한 사용 가능

### Boolean Type과의 관계
- 0은 거짓으로 판단
- 0이 아닌 모든 수는 참으로 판단

## Operation
```python
# 사칙 연산
c = a + b
c = a - b
c = a / b
c = a * b

# 사칙 연산의 확장
## 나눗셈의 확장
d = a % b ## 나머지 연산
d = a // b ## 몫 연산

## 곱셈의 확장
d = a ** 2 ## 계승 연산
```
- 사칙 연산과 그와 관련된 확장된 연산들을 사용 가능
- 나눗셈의 확장은 몫과 나머지 연산에 대한 표현
- 곱셈의 확장은 제곱 연산에 대한 표현

```python
a += 1
a *= 1
a %= 1
```
- 복합 연산자는 하나의 연산자로 변수에 연산을 수행한 후 대입할 수 있는 표현 방법

## Enumeric Type
- 하나의 변수에 복수의 값들이 저장
- Index나 Key를 활용해 Mapping된 변수를 참조 하는 형식으로 사용 가능

### List
```python
a = [ 1, 2, 3 ]
empty_list = []
empty_list2 = list()
```
- List의 선언은 `[]`괄호를 사용해 `,`로 구분된 요소를 나열해 선언하거나 `list()` 함수를 사용

```python
a[0]
a[-1]
a[:2]
```
- 저장된 복수 개의 변수들 중 Index를 사용해 참조
	-  `-1`을 사용하면 가장 마지막 Index의 값 참조 가능
- Slice: Index를 명시할 때 `[n:m]` 과 같이 범위를 나타내는 표현을 사용해 기존 List의 내용 일부를 새 List로 활용 가능
	- `[n:m]`으로 slicing 하는 경우 `n`번 index부터 `m-1`번 Index까지 포함
	- 처음을 표시하는 Index를 생략하는 경우 첫 번째 요소부터 반환
	- 마지막을 표시하는 Index를 생략하는 경우 마지막 요소 까지 반환

```python
b = [ 3, 4, "a" ]
```
- 서로 다른 Type의 변수도 하나의 LIst에 저장 가능

```python
a + [3, 4, 5]
a += [ 3, 4, 5 ]
a * 3
```
- 연산을 통해 list의 확장이 가능

```python
a.append(b)
a.remove(3)
a.insert(2, 1)
a.sort()
```
- 주요 List Type Method
	- `append` : List의 마지막 Index에 항목을 추가
	- `remove`: 특정 요소 제거
	- `insert`: 지정한 Index에 요소를 추가

```python
len(a)
```
- `len()` 함수를 사용하면 List의 총 길이( = List 마지막 Index의 `+1`)를 반환

### Tuple
```python
a = (1, 2, 3)
a[0]
a[-1]
a[:1]

b = (3, 4, 5)
a + b
a * 3
len(a)
```
- List와 유사하나 가장 큰 차이점으로는 기존 명시된 Tuple의 내용은 변경이 불가능 하다는 점
- `+`또는 `*`연산을 통해 새로운 Tuple을 생성하는 것은 가능

### Set
```python
a = {1, 2, 3}
b = {3, 4, 5}
```
- 집합을 나타내기 위한 변수형으로 내부적으로 순서를 구별하지 않아 Index를 통한 참조가 불가능

### Dictionary
```python
a = {
	 "key1": 1,
	 "key2": 2,
	}
a["key1"]
a["key2"] = 4
a["key3"] = 3
a["key4"] = [ 1, 3, 5 ]
len(a)
```
- Key와 Value로 구성된 자료형
- Index가 아닌 Key 값으로 Value를 참조
- Key로 Dictionary에 접근해 값을 대입하는 것으로 Value를 변경가능
	- 만약 Key가 없다면 새 Key가 Dictionary에 생성되어 Value가 Mapping
- `len()` 함수를 사용하면 Dictionary의 Key 개수를 반환

### String
```python
a = "string"
a[0]
a[1]
a[2:4]

b = " string2"
a + b
a * 2
```
- 1개 이상의 문자로 구성
- List와 유사하게 Index의 사용법이나 Slicing 사용 가능하며 동일한 방식으로 사칙연산 적용 가능
- 주로 사용하는 Method의 종류가 다름

```python
r"\n"

a = "asdf"
f"{a}"
```
- 여러가지 종류의 문자열
	- `r""`: Escape Sequence를 문자 그대로 출력하는 문자열
	- `f""`: Format 문자열로 문자열 내의 `{}` 내 변수명을 변수 값으로 대체해 출력해주는 문자열

## Type Casting
### String to int
```python
int("123")
int("0b001", 2)
int("0o56", 8)
int("0xff", 16)
int("1234", 12)
```
- `int()`함수를 사용
- 다른 진법의 문자열을 정수형으로 형변환 하는 경우 `base` 매개변수를 추가로 전달
	- 2, 8, 16 진법의 경우 Numeric Type 변수를 선언할 때와 동일하게 접두문자열을 추가하는 경우 해당 진법으로 변환하는 경우 에러 발생하지 않음
	- 2, 8, 16진법 이외의 진법으로도 변환 가능

### Int to string
```python
str(123)
bin(123)
oct(123)
hex(123)
```
- `str()`함수를 사용하는 경우 10진법의 숫자를 반환
- 2, 8, 16진법의 문자열로 변환하는 경우 각각에 맞는 함수를 사용

### List to string
```python
",".join([ "python", "list", "string" ])
```
- string 객체의 `join` Method를 사용
- 모든 요소들이 문자열일 경우에만 에러가 발생하지 않기 때문에 요소의 변수형에 대한 체크 필요

# Condition, Loop
## Conditional State
```python
if condition:
	# Something To Do
	a = 3
elif condition_2:
	b = 3
else:
	c = 3

if condition and condition_2:
	a = 4
if condition or condition_2:
	a = 5
if not condition:
	a = 6

```
- 특정 조건을 만족했을 때만 실행 시킬 내용을 작성할 때 사용
- 이때 `condition`은 Boolean Type의 변수이거나 Boolean Type을 Return하는 구문 또는 함수를 사용
- `if`이후 추가 조건 검사가 필요하다면 `elif`또는 `else` 구문을 사용
- `and`, `or`, `not`을 활용해 복수의 조건을 동시 적용하거나 NOT 연산을 활용 가능

### 비교 연산자
```python
a > b
a >= b
a == b
a != b
```
- 부등호와 등호 표시를 조합한 비교 연산자를 활용한 조건 구성

### Enumeric Type의 검사
```python
list_check = [1, 2, 3]
3 in list_check

dict_check = {
	"name": "John Doe",
	"age": 3
}
"name" in dict_check
"John Doe" in dict_chekc
```
- `in` 구문을 활용해 Enumeric Type 변수 요소를 판별 가능
- 특정 요소가 Enumeric Type 변수 내에 있는지 확인할 때 사용
- Dictionary Type의 경우 Value가 아닌 Key 값의 존재 여부를 확인

### Inline Conditional State를 활용한 3항 연산자
```python
a = 3 if condition else 4
```
- 3항연산자: 조건, 참인 경우의 값, 거짓인 경우의 값까지 3개의 항을 입력 받는 연산자
- `condition`이 조건항, `3`은 참인 경우의 값에 해당하는 항, `4`는 거짓인 경우의 값에 해당하는 항

## Loop
```python
for i in range(10):
	print(i)

list_values = [ 1, 2, 3, 4, 5 ]
for item in list_values:
	print(item)
while condition:
	print(i)
	i += 1
	
```
- for 구문은 Enumeric Type 변수를 참조해 변수의 Index를 순회 하며 값을 변수에 저장해 반환하는 방식으로 수행
- while 구문은 특정 조건이 참인 경우 Block 내의 내용을 계속 수행
	- 조건을 제대로 지정하지 않으면 무한 반복에 빠질 수 있으니 주의

### 반복문의 조작
- `break`: 해당 반복문 Block을 중단
- `continue`: 이후 내용은 수행하지 않고 다음 Step 수행

### Comprehension
```python
a = []
for i in range(10): a.append(i)
b = [ i * 10 for i in range(10) ]
```
- for 구문을 사용해 Enumeric Type 변수의 Item을 간단히 구성하는 방식
- List뿐만 아니라 Dictionary도 동일하게 적용가능
- 어떤 List의 요소 값에 조작을 가해 새로운 List를 만들 때 사용 가능

# Functions
## 선언과 호출
```python
def SomeFunc(_param1 = 0, _param2 = 0):
	ret = _param1 + _param2
	return ret

a = 2
b = 5
c = SomeFunc(a, b)
```
- 함수는`def` 구문으로 정의
- 매개변수는 없어도 무방
	- 매개 변수의 선언부에서 특정 값을 대입하는 표현을 사용하면 해당 매개변수가 입력되지 않았을 때 해당 값을 사용하여 작동
	- Default Value Parameter는 오른쪽 매개변수부터 적용 가능
- `return` 구문은 없어도 무방
- 호출은 함수의 이름과 전달할 매개변수를 `()`로 입력하며 Return 값이 있는 경우 다른 변수에 할당하며 호출 가능

## Named Parameter
```python
def NamedParams(_param1, _param2):
	return _param1 + _param2 * 2

print(NamedParams(_param1 = 2, _param2 = 3))
print(NamedParams(2, 3))
print(NamedParams(_param2 = 2, _param1 = 3))
```
- 함수의 매개변수 선언부에서 지정한 이름을 호출부에서 지정하며 값을 전달하는 방식
- 입력 순서와 상관없이 이름에 맞게 값이 입력되어 계산

### Format String
```python
format_string = "format area 1: {area_1}\n format area 2: {area_2}"
format_string.format(
	area_1 = "1st Value",
	area_2 = "2nd Value"
)
```
- f-string과 달리 `format` Method를 수행해야 String Formatting이 가능

## Enumeric Type to Linear Parameter
```python
def TupleInput(_n1, _n2):
	return _n1 + _n2 * 2

tpA = (1, 2)
a = TupleInput(tpA)
a = TupleInput(*tpA)
```
- Enumeric Type 변수의 항목을 함수의 매개변수로 전달하기 위해서 사용하는 방법
- `*`기호를 Enumeric Type 변수 이름 앞에 붙여 매개변수로 전달하면 요소들을 앞 매개변수 부터 각각 대응되는 위치에 전달

### 다중 매개변수의 활용 
```python
def TupleConv(*tpA):
	for i in tpA:
		print(i)

TuleConv(1, 2, 3, 4)
TuleConv(1, 3)
```
- 여러 매개 변수를 받아야 할 때 개수를 정하지 않고 받아야 하는 경우 사용
- 함수의 정의부에서 매개변수 선언 시 `*`를 붙여 선언할 경우 해당 매개변수를 함수 내에서 Tuple과 같이 활용 가능

# Class
```python
class Info:
	def __init__(self, _name, _address):
		self.name = _name
		self.addr = _address

	def Rename(self, _new_name):
		self.name = _new_name

	def isNamed(self):
		return self.name != ""
```
- `class` 키워드로 선언 가능
- `__init__`은 예약된 Method 이름으로 객체가 생성될 때 호출되는 생성자 Method로 객체 속성의 정의부
- 개별 Method 정의 시 매개변수로 `self`를 사용해 객체 내 속성 값을 참조 가능

```python
my_info = Info("test", "192.168.0.1")

my_info.name = "test2"
my_info.Rename("")

if my_info.isNamed():
	print("Name is Empty")
```
- 객체의 생성은 Class의 이름과 생성자에 필요한 매개변수를 전달
- 객체의 속성 참조는 객체의 변수명과 속성의 이름을 사용
- 객체의 Method 사용은 속성 참조와 마찬가지로 객체의 변수명과 Method 이름, 필요한 경우 Method의 매개변수를 전달

# Import Modules/Library
```python
import os
from threading import Thread
```
- `import` 키워드와 모듈 이름을 사용하는 것이 기본적인 사용방법
- 모듈 내의 특정 Class, 함수, 상수 등의 일부분만 Import하는 경우 `from` 키워드와 함께 사용

## Module Alias
```python
import numpy as np
from pandas import Dataframe as df 
```
- Module 또는 Import 대상의 뒤에 `as` 키워드를 사용
- 해당 요소를 참조할 때 Alias를 설정한 키워드로 사용 가능

# File I/O
```python
file_opened = open(file_path, open_mode)
# Something File IO
file.close()

with open(file_path, open_mode) as file_opened:
	# somethin File IO
```
- 전달받은 경로의 파일을 참조해 Mode에 맞게 파일을 처리하는 방식
- Mode는 읽기/쓰기/추가를 표시하고, Binary 여부를 표시하고, 파일이 없는 경우 생성하도록 표시하는 3부분으로 구성
	- 의미
		- 읽기: `r`
		- 쓰기: `w`
		- 추가: `a`
		- Binary: `b`
		- 생성: `+`
	- 사용예
		- `r`: 파일을 읽기 모드로 열기
		- `w+`: 파일이 없다면 생성하고, 파일이 이미 있는 경우에도 내용을 덮어쓰기
		- `a+`: 파일이 없다면 생성하고, 이미 있는 파일 뒤에 내용을 이어 작성
		- `wb`: Binary 데이터를 덮어쓰기
- ASCII 파일의 경우 Binary 여부를 생략
- 파일이 없을 때 에러를 발생하게 하고 싶다면 생성 모드를 생략
- Open된 파일은 Close를 해주지 않으면 손상 될 수 있으나 `with`구문을 사용하는 경우 별도의 Close 구문 불필요

## Handle CSV File
```python
import csv
```
- Python 설치 할 때 기본으로 설치되는 모듈
- Import  필요

### Read CSV
```python
with open(strPathCSV, "r") as fileCSV:
	csvTarget = csv.reader(
		fileCSV,
		delimiter = ","
	)
	for line in csvTarget:
		print(line)
```
- `csv.reader()` 함수를 사용해 객체 생성
- 객체는 바로 Enumeric Type 변수와 같이 사용 가능
- 위 `for` 반복문에서 `line`변수는 문자열을 요소로 갖는 List Type 변수

### Write CSV
```python
with open(strPathCSV, "w+", newline = "", encoding = "utf8") as fileCSV:
	csvTarget = csv.writer(
		fileCSV,
		delimiter = ","
	)
	csvTarget.writerow([1, 2, 3])
```
- `csv.writer()` 함수를 사용해 객체 생성
	- `delimiter`: CSV 파일 내부에서 사용할 구분자
- `writerow()` Method를 사용해 매개변수로 입력한 리스트를 파일에 입력


---
#python #in-workspace
