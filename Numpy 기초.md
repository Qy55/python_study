# Before this content
- numpy 주요 내용: 행렬 연산 및 참조에 대한 사용하기 쉬운 인터페이스 제공
- 행렬 사용 이전에 2차원 배열의 사용에 대한 내용 사전 학습 필요

## 2 Dimension array
```python
arr2d = [
	[ 1, 2, 3, 4, 5 ],
	[ 2, 3, 4, 5, 6 ],
	[ 3, 4, 5, 6, 7 ],
	[ 4, 5, 6, 7, 8 ],
	[ 5, 6, 7, 8, 9 ]
]

arr2d_comp = [
	 [ i + j for i in range(5) ] for j in range(5)
]
```
- 요소로 (1차원) List를 가지는 List
- Comprehension을 사용한 2차원 배열의 초기화 방법

### Index & Slice
```python
arr2d[1][3]
arr2d[0][:3]
arr2d[:4]
for row in arr2d[1:4]: print(row[1:4])
```
- 바깥 List의 참조 후 내부 List를 참조를 이어서 수행
- 참조 시 반환되는 값의 Type이 Enumeric Type이라면 이후 Index를 통한 참조 가능

# Install Package & Import
```bash
python3 -m pip install numpy
```
- 터미널에서 수행

```python
import numpy as np
```
- ` ~ as np` 구문은 일반적으로 사용

# Initialize
## From list
```python
arr1d = np.array([1, 2, 3])
arr2d = np.array(
    [[1, 2, 3],
     [4, 5, 6]])
arr3d = np.array(
    [
        [
            [1, 2, 3],
            [2, 3, 4],
            [2, 3, 4]
        ],
        [
            [3, 4, 5],
            [4, 5, 6],
            [4, 5, 6]
        ],
        [
            [1, 2, 3],
            [2, 3, 4],
            [2, 3, 4]
        ]
    ]
)
```
- 1, 2, 3차원 배열을 생성하는 방법
- `arr.shape` Attribute를 확인하면 행렬의 크기와 모양 파악 가능

## Using Funtions
### Specified size
```python
arrZeros1d = np.zeros(3)
arrZeros2d = np.zeros((5, 5))
arrOnes3d = np.ones((3, 3, 3))

arrEye3 = np.eye(3)
```
- `zeros`: 0으로 채워진 행렬을 생성
- `ones`: 1로 채워진 행렬을 생성
- `eye`: 2차원 항등행렬을 생성

### Vector
```python
arrArange_1_10 = np.arange(1, 10)
arrArange_step = np.aragen(1, 10, 2)
arrAragne_nparam = np.arange(start = 1, stop = 10, step = 2, dtype = type(1) )

arrLinspace = np.linspace(1, 10)
arrLinspace_num = np.linspace(1, 10, 5)
arrLinspace_nparam = np.linspace(start = 1, stop = 10, num = 7, dtype = int)
```
- `arange`: `start`이상 `stop`이하의 수 중 `step`을 공차로 하는 등차차수열을 반환. 단, 마지막 항과 공차를 더 했을 떄 `stop`을 넘어간다면 굳이 수열에 `stop`을 포함하지 않음
- `linspace`:  Linear Scale의 공간에서 `start`이상 `stop`이하를 균등하게 `num`개만큼 분할해 각각의 수를 정의역으로 가지는 치역. 반드시 `start`와 `stop`이 정의역에 포함되어 계산

### Copy size from other array
```python
arrZerosLike = np.zeros_like(arr2d)
arrOneslike = np.ones_like(arr2d)
```
- 이미 생성된 행렬의 크기와 동일한 크기의 행렬 생성

# Index
## In Vector Matrix
```python
arr1d = np.linspace(1, 10, 5)

arr1d[0]
arr1d[1:3]
```
- 일반적인 List와 마찬가지로 Index 참조 및 Slice 가능
### Filtering
```python
lstFilter = [ i % 2 == 0 for i in range(len(arr1d))]
arr1d[lstFilter]
```
- 동일한 길이를 가지며 요소가 전부 Boolean Type 인 List를 Index에 적용하면 Filter로 작동
- Filter List의 `True`인 Index와 같은 Index에 있는 대상 행렬의 값만 List로 반환
- Filter List의 `True`개수와 반환되는 행렬의 길이는 동일

```python
arr1d > 3
arr1d[arr1d > 3]
```
- 부등호를 행렬에 적용하면 Filtering Vector Matrix를 생성 가능

## In Matrix
```python
lstInput = [
	[ 1, 2, 3, 4, 5 ],
	[ 2, 3, 4, 5, 6 ],
	[ 3, 4, 5, 6, 7 ],
	[ 4, 5, 6, 7, 8 ],
	[ 5, 6, 7, 8, 9 ]
]
arr2d = np.array(input)

arr2d[2, 3]
arr2d[2][3]
arr2d[1:4,3]
arr2d[1:4,1:4]
```
- `[2, 3]`와 `[2][3]`는 동일한 Index를 의미
- `,`를 이용한 Index 적용 시에도 동일하게 Slice 표현을 사용할 수 있으며 좌표 별로 각각 적용 가능
### Filtering
```python
arr2d > 3
arr2d[arr2d > 3]
arr2d[(arr2d > 2) & (arr2d < 5)]
```
- Vector에 적용하는 것과 동일하게 사용 가능
- 복수 개의 필터 적용 시에는 각 조건을 괄호`()`로 감싸주어야 적용 가능
- 반환 되는 행렬은 1차원

---
#python #in-workspace 