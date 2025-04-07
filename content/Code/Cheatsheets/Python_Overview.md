---
tags:
  - cheatsheet
  - reference
  - python
aliases:
  - Python Cheatsheet
  - Python Overview
date: 2025-03-29
---
# Python Cheatsheet

# 1. VARIABLES & DATA TYPES
```
x = 10             # Integer
y = 3.14          # Float
name = "Alice"    # String
is_valid = True   # Boolean
nums = [1, 2, 3]  # List
data = (1, 2, 3)  # Tuple
info = {"key": "value"}  # Dictionary
unique = {1, 2, 3} # Set
```

# 2. BASIC OPERATORS
```

add = 5 + 2      # 7
sub = 5 - 2      # 3
mul = 5 * 2      # 10
div = 5 / 2      # 2.5
floor_div = 5 // 2  # 2
mod = 5 % 2      # 1
power = 2 ** 3   # 8
```
# 3. CONDITIONALS
```
if x > 5:
    print("x is large")
elif x == 5:
    print("x is 5")
else:
    print("x is small")
```
# 4. LOOPS
```
for i in range(5):  # 0,1,2,3,4
    print(i)

while x > 0:
    x -= 1  # Decrease x
```
# 5. LIST COMPREHENSION
```
squared = [i**2 for i in range(5)]  # [0, 1, 4, 9, 16]
```
# 6. FUNCTIONS
```
def greet(name="User"):
    return f"Hello, {name}!"

print(greet("Bob"))  # Hello, Bob!
```
# 7. LAMBDA FUNCTION
```
square = lambda x: x ** 2
print(square(4))  # 16
```
# 8. EXCEPTION HANDLING
```
try:
    res = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```
# 9. CLASSES
```
class Person:
    def __init__(self, name):
        self.name = name

    def say_hello(self):
        return f"Hi, I'm {self.name}!"

p = Person("Alice")
print(p.say_hello())  # Hi, I'm Alice!
```
# 10. FILE HANDLING
```
with open("file.txt", "w") as f:
    f.write("Hello, World!")

with open("file.txt", "r") as f:
    content = f.read()
```
# 11. DICTIONARY OPERATIONS
```
info = {"name": "Alice", "age": 25}
info["city"] = "NY"
print(info.get("name"))  # Alice
```
# 12. LIST METHODS
```
nums.append(4)     # [1,2,3,4]
nums.remove(2)     # [1,3,4]
nums.sort()        # [1,3,4]
nums.reverse()     # [4,3,1]
```
# 13. IMPORTING MODULES
```
import math
print(math.sqrt(16))  # 4.0

from random import randint
print(randint(1, 10))  # Random number between 1-10
```
# 14. ENUMERATE & ZIP
```
for idx, val in enumerate(["a", "b", "c"]):
    print(idx, val)  # 0 a, 1 b, 2 c

names = ["Alice", "Bob"]
ages = [25, 30]
for name, age in zip(names, ages):
    print(name, age)  # Alice 25, Bob 30
```