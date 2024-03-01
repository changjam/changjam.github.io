In Python, there are several common data structures, some of which include:

### 1. List
A list is an ordered collection that can contain elements of various types. It is one of the most commonly used data structures.

#### Common functionalities:
- `append()`: Add elements to the end of the list.
- `extend()`: Add elements from another list to the list.
- `insert()`: Insert an element at a specified position.
- `remove()`: Remove a specific value from the list.
- `pop()`: Remove and return an element at a specified position.
- `index()`: Return the index of a specified value.
- `count()`: Return the number of occurrences of a specified value.
- `sort()`: Sort the list.
- `reverse()`: Reverse the order of elements in the list.

```python
# Example code:
my_list = [1, 2, 3, 4, 5]

# Add elements
my_list.append(6)
print(my_list)  # [1, 2, 3, 4, 5, 6]

# Insert elements
my_list.insert(2, 2.5)
print(my_list)  # [1, 2, 2.5, 3, 4, 5, 6]

# Remove elements
my_list.remove(2.5)
print(my_list)  # [1, 2, 3, 4, 5, 6]

# Sort
my_list.sort()
print(my_list)  # [1, 2, 3, 4, 5, 6]
```

### 2. Dictionary
A dictionary is an unordered collection of key-value pairs, where each key is associated with a value.

#### Common functionalities:
- `keys()`: Return a list of all keys.
- `values()`: Return a list of all values.
- `items()`: Return a list of all key-value pairs as tuples.
- `get()`: Get the value corresponding to a key, or return a default value if the key does not exist.
- `pop()`: Remove the item with the specified key and return its value.

```python
# Example code:
my_dict = {'a': 1, 'b': 2, 'c': 3}

# Get all keys
print(my_dict.keys())  # dict_keys(['a', 'b', 'c'])

# Get all values
print(my_dict.values())  # dict_values([1, 2, 3])

# Get all key-value pairs
print(my_dict.items())  # dict_items([('a', 1), ('b', 2), ('c', 3)])

# Get value by key
print(my_dict.get('b'))  # 2

# Remove specified key
my_dict.pop('b')
print(my_dict)  # {'a': 1, 'c': 3}
```

### Common functions:
- `len()`: Return the length of a container.
- `sorted()`: Return a sorted container.
- `max()`: Return the maximum value in a container.
- `min()`: Return the minimum value in a container.
- `sum()`: Return the sum of all elements in a container.

```python
# Example code:
my_list = [3, 1, 5, 2, 4]

# Return the length of the list
print(len(my_list))  # 5

# Return the maximum value in the list
print(max(my_list))  # 5

# Return the minimum value in the list
print(min(my_list))  # 1

# Return the sum of all elements in the list
print(sum(my_list))  # 15
```

The above is an introduction to common data structures and functions in Python, along with related code examples. These data structures and functions are fundamental and commonly used parts of Python programming, and are very useful for handling various problems and tasks.