Python 中有多種常見的資料結構，其中一些包括：

### 1. 列表 (List)
列表是一個有序的集合，可以包含各種類型的元素。它是最常用的資料結構之一。

#### 常用功能：
- `append()`: 在列表末尾添加元素。
- `extend()`: 將另一個列表中的元素添加到列表中。
- `insert()`: 在指定位置插入元素。
- `remove()`: 刪除列表中的特定值。
- `pop()`: 刪除並返回指定位置的元素。
- `index()`: 返回指定值的索引。
- `count()`: 返回指定值的出現次數。
- `sort()`: 對列表進行排序。
- `reverse()`: 對列表進行反轉。

```python
# 示例程式碼：
my_list = [1, 2, 3, 4, 5]

# 添加元素
my_list.append(6)
print(my_list)  # [1, 2, 3, 4, 5, 6]

# 插入元素
my_list.insert(2, 2.5)
print(my_list)  # [1, 2, 2.5, 3, 4, 5, 6]

# 刪除元素
my_list.remove(2.5)
print(my_list)  # [1, 2, 3, 4, 5, 6]

# 排序
my_list.sort()
print(my_list)  # [1, 2, 3, 4, 5, 6]
```

### 2. 字典 (Dictionary)
字典是一種無序的鍵-值對集合，每個鍵都與一個值相關聯。

#### 常用功能：
- `keys()`: 返回所有鍵的列表。
- `values()`: 返回所有值的列表。
- `items()`: 返回所有鍵-值對的元組列表。
- `get()`: 根據鍵取得對應的值，如果鍵不存在則返回預設值。
- `pop()`: 刪除指定鍵的項目並返回其值。

```python
# 示例程式碼：
my_dict = {'a': 1, 'b': 2, 'c': 3}

# 取得所有鍵
print(my_dict.keys())  # dict_keys(['a', 'b', 'c'])

# 取得所有值
print(my_dict.values())  # dict_values([1, 2, 3])

# 取得所有鍵-值對
print(my_dict.items())  # dict_items([('a', 1), ('b', 2), ('c', 3)])

# 根據鍵取得值
print(my_dict.get('b'))  # 2

# 刪除指定鍵
my_dict.pop('b')
print(my_dict)  # {'a': 1, 'c': 3}
```

### 常用函數：
- `len()`: 返回容器的長度。
- `sorted()`: 返回排序後的容器。
- `max()`: 返回容器中的最大值。
- `min()`: 返回容器中的最小值。
- `sum()`: 返回容器中所有元素的和。

```python
# 示例程式碼：
my_list = [3, 1, 5, 2, 4]

# 返回列表的長度
print(len(my_list))  # 5

# 返回列表中的最大值
print(max(my_list))  # 5

# 返回列表中的最小值
print(min(my_list))  # 1

# 返回列表中所有元素的和
print(sum(my_list))  # 15
```

以上是 Python 中常見的資料結構和常用函數的簡介及相關程式碼示例。這些資料結構和函數是 Python 編程中非常基礎和常見的一部分，對於處理各種問題和任務都非常有用。