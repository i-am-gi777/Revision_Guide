# 01-introduction
Python Basics:
What is Python?
High-level, interpreted, dynamically typed, and easy to read.
Features:
Open-source, portable, extensive libraries, object-oriented, etc.
Hello World:
```python
print("Hello, World!")

# 02-variables-and-datatypes

 Variables: Containers for storing data values.
```python
x = 5                                      # integer
name = "Alice"                             # string

# Data Types:
# int, float, str, bool, list, tuple, set, dict, NoneType
type(x)

 1. Numeric Types
 x = 10                                     # int
y = 3.14                                    # float
z = 2 + 3j                                  # complex
print(x)                                    # Output: 10
print(y)                                    # Output: 3.14
print(z)                                    # Output: 2+3j
print(type(x))                              # <class 'int'>
print(type(y))                              # <class 'float'>
print(type(z))                              # <class 'complex'>

2. Sequence Types
name = "Alice"                              # str
numbers = [1, 2, 3]                         # list
coords = (10, 20)                           # tuple
print(name)                                 # Output: Alice
print(numbers)                              # Output: [1, 2, 3]
print(coords)                               # Output: (10, 20)
print(type(name))                           # <class 'str'>
print(type(numbers))                        # <class 'list'>
print(type(coords))                         # <class 'tuple'>

3. Set Types
id_numbers = {1,2,3,7}                      # set
print(id_numbers)                           # Output: {1, 2, 3}
print(type(id_numbers))                     # <class 'set'>

4.Mapping Type
person = {"name": "Bob", "age": 30}         # dict
print(person["name"])                       # Output: Bob
print(type(person))                         # <class 'dict'>

5. Boolean Type
valid = True                                # bool
print(valid)                                # Output: True
print(type(is_valid))                       # <class 'bool'>

6. None Type
result = None
print(type(result))                         # <class 'NoneType'>

Types of Operators:
Arithmetic: +, -, *, /, //, %, **
Comparison: ==, !=, >, <, >=, <=
Logical: and, or, not
Assignment: =, +=, -=, etc.
Membership: in, not in
Identity: is, is not


# Python Operators

Operators are used to perform operations on variables and values.

---

1. Arithmetic Operators

| Operator | Description           | Example         |
|----------|-----------------------|-----------------|
| `+`      | Addition              | `3 + 2 → 5`     |
| `-`      | Subtraction           | `5 - 2 → 3`     |
| `*`      | Multiplication        | `4 * 3 → 12`    |
| `/`      | Division              | `10 / 2 → 5.0`  |
| `//`     | Floor Division        | `7 // 2 → 3`    |
| `%`      | Modulus (remainder)  | `7 % 2 → 1`     |
| `**`     | Exponentiation        | `2 ** 3 → 8`    |


```python
a = 10
b = 3

print(a + b)  # 13
print(a - b)  # 7
print(a * b)  # 30
print(a / b)  # 3.333...
print(a // b) # 3
print(a % b)  # 1
print(a ** b) # 1000

2. Comparison (Relational) Operators
Used to compare two values and return a boolean (True or False).

| Operator | Description      | Example         |
| -------- | ---------------- | --------------- |
| `==`     | Equal to         | `5 == 5 → True` |
| `!=`     | Not equal to     | `5 != 3 → True` |
| `>`      | Greater than     | `7 > 3 → True`  |
| `<`      | Less than        | `2 < 5 → True`  |
| `>=`     | Greater or equal | `5 >= 5 → True` |
| `<=`     | Less or equal    | `4 <= 6 → True` |


x = 7
y = 5

print(x == y)  # False
print(x != y)  # True
print(x > y)   # True
print(x < y)   # False
print(x >= 7)  # True
print(x <= 10) # True

3. Logical Operators
Used to combine conditional statements.

| Operator | Description            | Example          |
| -------- | ---------------------- | ---------------  |
| `and`    | True if both are True  | `True and False →False`|
| `or` | True if at least one is True| `True or False →True` |
| `not`| Negates the result      | `not True → False`        |

a = 10
b = 5

print(a > 5 and b < 10)   # True
print(a < 5 or b < 10)    # True
print(not (a == b))       # True

4. Assignment Operators
Used to assign values to variables.
| Operator | Description         | Example                |
| -------- | ------------------- | ---------------------- |
| `=`      | Assign              | `x = 5`                |
| `+=`     | Add and assign      | `x += 3` → `x = x + 3` |
| `-=`     | Subtract and assign | `x -= 2`               |
| `*=`     | Multiply and assign | `x *= 4`               |
| `/=`     | Divide and assign   | `x /= 2`               |
| `//=`    | Floor divide        | `x //= 2`              |
| `%=`     | Modulus             | `x %= 3`               |
| `**=`    | Exponentiation      | `x **= 2`              |


 x = 10
x += 5    # x = 15
x *= 2    # x = 30
x //= 4   # x = 7
print(x)


5. Membership Operators
Used to test if a value is part of a sequence (like list, string, etc.)

| Operator | Description          | Example            |
| -------- | -------------------- | ------------------ |
| `in`  | True if value exists | `'a' in 'apple' → True`     |
| `not in`| True if not exists | `'x' not in 'apple' → True` |

fruits = ["apple", "banana", "cherry"]

print("apple" in fruits)     # True
print("grape" not in fruits) # True

6. Identity Operators

Used to compare memory locations (identity) of two objects.
| Operator | Description                       | Example    |
| -------- | --------------------------------- | --------- |
| `is`     | True if both refer to same object | `a is b`   |
| `is not` | True if not same object           | `a is not b`|


a = [1, 2]
b = a
c = [1, 2]

print(a is b)     # True (same memory)
print(a is c)     # False (same value, different object)
print(a == c)     # True (same value)
print(a is not c) # True





