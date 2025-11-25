# PYTHON

- Python is a `High-Level Language` (one that is clode to human language and far from machine language. Here, no need to worry about memory address, regusters or binary code)
- Python is an `Interpreted Language` (code is executed `line-by-line` by an interpreter)
- When you run a Python program:
  - Python source code (`.py`) → compiled into bytecode (`.pyc`).
  - Bytecode is then executed by the Python interpreter (`PVM` – Python Virtual Machine) line by line.

## Typecasting

### List ↔ Dictionary
- ```py
    list1 = [1, 2, 3, 4]
    dict1 = dict(list1)   # ERROR
  ```
Reason: The `dict()` is a constructor that expects arrguments in pairs(key, value), not just single numbers
- Valid Ways:
  - **List of tuples**(key, value)
  ```py
  listt = [(1, 'a'), (2,'b'), (3,'c'), (4, 'd')]
  dictt = dict(listt)
  print(dictt)
  
  # {1: 'a', 2: 'b', 3: 'c'}
  ```
  - **Two lists (keys & values) → zip()**
    - `zip()` is like a stapler. When we have multiple lists, it ties the items at same position (same index) into a tuple 
    - `zip()` pairs items by their index and stops when the shortest list runs out
  ```py
  list_key = [1, 2, 3, 4]
  list_value = ['a', 'b', 'c', 'd']
  dictt = dict(zip(list_key, list_value))
  print(dictt)

  # {1: 'a', 2: 'b', 3: 'c', 4: 'd'}
  ```
  - **Using Dictionary Comprehension**:
    ```py
    listt = [1, 2, 3, 4]
    dictt = {x: x**2 for x in listt}  # example mapping
    print(dictt)

    # {1: 1, 2: 4, 3: 9, 4: 16}
    ```

### Dictionary ↔ List
    ```py
    dict1 = {1: 'a', 2: 'b'}

    list_keys = list(dict1.keys())      
    # [1, 2]
    # It gives all the keys
    list_values = list(dict1.values())  
    # ['a', 'b']
    # It gives all the values
    list_items = list(dict1.items())    
    # [(1, 'a'), (2, 'b')]
    ```


### 