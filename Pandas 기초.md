# Install
```bash
python -m pip install pandas
```

```python
import pandas as pd
# from pandas import dataframe as df
```
# Initialize
## From Array
```python
columns = ['Name',    'Age', 'City']
data = [  ['Alice',   24,    'New York'],
         ['Bob',     27,    'Los Angeles'],
         ['Charlie', 22,    'Chicago'],
         ['David',   32,    'Houston']
]

df = pd.DataFrame(data, columns=columns)
```

## From Dictionary
```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David'],
    'Age': [24, 27, 22, 32],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston']
}

df = pd.Dataframe(data)
```

## From CSV File
- `open()`함수를 사용하지 않고 참조
```python
df = pd.read_csv('data.csv')
```

# Handle Dataframe
## Handle Columns
### Index/Key Reference
```python
df['Name']
df.iloc[1]
```
- Column 이름에 해당하는 Key를 통한 참조 가능
- Dataframe의 `iloc` Attribute를 사용하면 Key의 Index를 통한 참조 가능

### Add
```python
df['Occupation'] = ['Engineer', 'Doctor', 'Artist', 'Chef']
```
- Dictionary와 비슷하게 사용 가능
- 추가할 Column을 Key로 사용하며 현재 Dataframe에 있는 Row의 개수 만큼 List에 요소를 구성해 할당
### Modify
```python
df['Age'] = df['Age'] + 1
```
- Key로 지정된 Column의 모든 값에 대해 연산 수행행
## Concatenate
```python
data2 = {
    'Name': ['Eve', 'Frank'],
    'Age': [28, 26],
    'City': ['San Francisco', 'Seattle'],
    'Occupation': ['Lawyer', 'Teacher']
}

df2 = pd.DataFrame(data2)
combined_df = pd.concat([df, df2], ignore_index=True)
```
- 두 Dataframe의 데이터를 결합

## Filtering
```python
older_than_25 = df[df['Age'] > 25]
```
- numpy에서 사용하던 Filter 방식과 유사하게 적용 가능

## Sort
```python
sorted_by_age = df.sort_values(by='Age')
sorted_by_name_desc = df.sort_values(by='Name', ascending=False)
```
- `sort_values()` Method를 사용해 정렬된 Dataframe 반환
- `ascending` 매개변수를 통해 오름차순/내림차순을 설정 가능능

## Info & Summary
```python
df.info()
df.describe()
grouped_by_city = df.groupby('City').mean()
city_counts = df['City'].value_counts()
```

# Export data
## To physical file
```python
df.to_excel("./data.xlsx", index=False)
df.to_csv('data.csv', index=False)
df.to_json('data.json', orient='records')
df.to_html('data.html', index=False)
```
- 각 데이터 표현 형식별 여러 확장자를 지원
- `index` 매개변수는 파일로 저장할 때 가장 왼쪽 열에 Index값 표시 여부
- JSON으로 Export 하는 Method의 `orient` 매개 변수는 데이터 저장 형식을 표시
	- `split`, `records`, `index`, `columns`, `values`, `table` 값 사용 가능
## Using sqlite3
```python
import sqlite3

# SQLite 데이터베이스에 저장
conn = sqlite3.connect('data.db')
df.to_sql('people', conn, if_exists='replace', index=False)
conn.close()
```
- `if_exists`는 지정한 테이블이 이미 존재할때의 동작을 지정
	- `fail`, `replace`, `append` 사용 가능

# About NaN
```python

```

## Replace NaN
```python

```

---
#python #in-workspace