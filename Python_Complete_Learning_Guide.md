# Python Learning Guide: From Basics to Advanced

## Overview
This notebook covers Python programming concepts from fundamentals to advanced topics, with practical examples and exercises to practice.

---

# Part 1: Python Basics

## 1.1 Variables and Data Types

### Variables
- Container for storing data values
- No need to declare type explicitly (dynamic typing)
- Naming convention: snake_case for variables

### Primary Data Types
1. **int**: Integer numbers (e.g., 10, -5, 0)
2. **float**: Decimal numbers (e.g., 3.14, -2.5)
3. **str**: Text/strings (e.g., "Hello", 'Python')
4. **bool**: Boolean values (True, False)
5. **NoneType**: None (absence of value)

```python
# Example: Variables and Data Types

# Integer
age = 25
print(f"Age: {age}, Type: {type(age)}")

# Float
height = 5.9
print(f"Height: {height}, Type: {type(height)}")

# String
name = "Alice"
print(f"Name: {name}, Type: {type(name)}")

# Boolean
is_student = True
print(f"Is Student: {is_student}, Type: {type(is_student)}")

# None
result = None
print(f"Result: {result}, Type: {type(result)}")
```

## 1.2 Operators

### Arithmetic Operators
- `+` : Addition
- `-` : Subtraction
- `*` : Multiplication
- `/` : Division (returns float)
- `//`: Floor Division (returns integer)
- `%` : Modulo (remainder)
- `**`: Exponentiation (power)

### Comparison Operators
- `==` : Equal to
- `!=` : Not equal to
- `>` , `<` : Greater/Less than
- `>=`, `<=`: Greater/Less than or equal

### Logical Operators
- `and` : Both conditions true
- `or` : At least one condition true
- `not` : Negation

```python
# Example: Operators

# Arithmetic
a, b = 10, 3
print(f"Addition: {a + b}")
print(f"Division: {a / b}")
print(f"Floor Division: {a // b}")
print(f"Modulo: {a % b}")
print(f"Power: {a ** b}")

# Comparison
print(f"\n10 == 10: {10 == 10}")
print(f"10 > 5: {10 > 5}")

# Logical
x = 5
print(f"\n(x > 3) and (x < 10): {(x > 3) and (x < 10)}")
print(f"(x > 10) or (x < 3): {(x > 10) or (x < 3)}")
print(f"not (x > 10): {not (x > 10)}")
```

# Part 2: Control Flow

## 2.1 Conditional Statements (if/elif/else)

- Execute code based on conditions
- Indentation is crucial in Python
- Use `if`, `elif`, `else` keywords

```python
# Example: Conditional Statements

score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "F"

print(f"Score: {score}, Grade: {grade}")

# Ternary operator
age = 18
status = "Adult" if age >= 18 else "Minor"
print(f"Age: {age}, Status: {status}")
```

## 2.2 Loops

### for loop
- Iterate over sequences (list, tuple, string, range)
- Use `break` to exit loop
- Use `continue` to skip iteration

### while loop
- Execute while condition is true
- Risk of infinite loop

```python
# Example: for loop

print("For loop - Print numbers 1 to 5:")
for i in range(1, 6):
    print(i, end=" ")
print()

# Iterate over list
fruits = ["apple", "banana", "cherry"]
print("\nFruits:")
for fruit in fruits:
    print(f"  - {fruit}")

# with index
print("\nFruits with index:")
for index, fruit in enumerate(fruits):
    print(f"  {index}: {fruit}")
```

```python
# Example: while loop

count = 0
print("While loop - Count to 5:")
while count < 5:
    count += 1
    print(count, end=" ")
print()

# break and continue
print("\nWith break (stop at 3):")
for i in range(1, 6):
    if i == 3:
        break
    print(i, end=" ")
print()

print("\nWith continue (skip 3):")
for i in range(1, 6):
    if i == 3:
        continue
    print(i, end=" ")
print()
```

# Part 3: Data Structures

## 3.1 Lists

- Ordered, mutable collection
- Can contain mixed data types
- Indexed from 0
- Methods: append, extend, insert, remove, pop, sort, reverse

```python
# Example: Lists

# Create list
numbers = [1, 2, 3, 4, 5]
print(f"List: {numbers}")

# Access elements
print(f"First element: {numbers[0]}")
print(f"Last element: {numbers[-1]}")
print(f"Slice [1:4]: {numbers[1:4]}")

# Modify list
numbers.append(6)
print(f"After append(6): {numbers}")

numbers.extend([7, 8, 9])
print(f"After extend([7,8,9]): {numbers}")

numbers.insert(0, 0)
print(f"After insert(0, 0): {numbers}")

numbers.remove(3)
print(f"After remove(3): {numbers}")

# List comprehension
squares = [x**2 for x in range(1, 6)]
print(f"Squares: {squares}")
```

## 3.2 Tuples

- Ordered, immutable collection
- Similar to lists but cannot be modified
- Faster than lists
- Often used as dictionary keys

```python
# Example: Tuples

# Create tuple
coordinates = (10, 20, 30)
print(f"Tuple: {coordinates}")

# Access elements
print(f"First element: {coordinates[0]}")

# Unpacking
x, y, z = coordinates
print(f"Unpacked: x={x}, y={y}, z={z}")

# Tuples are immutable
try:
    coordinates[0] = 5
except TypeError as e:
    print(f"Error: {e}")
```

## 3.3 Dictionaries

- Unordered, mutable collection of key-value pairs
- Keys must be unique and immutable
- Values can be any data type
- Accessed by keys, not indexes

```python
# Example: Dictionaries

# Create dictionary
person = {
    "name": "Alice",
    "age": 30,
    "city": "New York",
    "hobbies": ["reading", "hiking"]
}
print(f"Dictionary: {person}")

# Access values
print(f"Name: {person['name']}")
print(f"Age: {person.get('age')}")

# Modify dictionary
person['age'] = 31
person['email'] = 'alice@example.com'
print(f"\nAfter modification: {person}")

# Dictionary methods
print(f"\nKeys: {person.keys()}")
print(f"Values: {person.values()}")
print(f"Items: {person.items()}")

# Iterate
print("\nIterate over items:")
for key, value in person.items():
    print(f"  {key}: {value}")
```

## 3.4 Sets

- Unordered, mutable collection of unique elements
- No duplicates allowed
- Cannot access by index
- Useful for mathematical operations (union, intersection, difference)

```python
# Example: Sets

# Create set
numbers = {1, 2, 3, 4, 5, 5, 5}
print(f"Set: {numbers}")  # Duplicates removed

# Add and remove
numbers.add(6)
print(f"After add(6): {numbers}")

numbers.remove(3)
print(f"After remove(3): {numbers}")

# Set operations
set_a = {1, 2, 3, 4}
set_b = {3, 4, 5, 6}

print(f"\nSet A: {set_a}")
print(f"Set B: {set_b}")
print(f"Union: {set_a | set_b}")
print(f"Intersection: {set_a & set_b}")
print(f"Difference: {set_a - set_b}")
print(f"Symmetric Difference: {set_a ^ set_b}")
```

# Part 4: Functions

## 4.1 Function Basics

- Reusable block of code
- Defined with `def` keyword
- Can have parameters and return values
- Naming convention: snake_case

```python
# Example: Basic Functions

# Function with no parameters
def greet():
    print("Hello, World!")

greet()

# Function with parameters
def add(a, b):
    return a + b

result = add(5, 3)
print(f"5 + 3 = {result}")

# Function with default parameters
def greet_person(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet_person("Alice"))
print(greet_person("Bob", "Hi"))

# Function with *args (variable arguments)
def sum_all(*numbers):
    return sum(numbers)

print(f"Sum: {sum_all(1, 2, 3, 4, 5)}")

# Function with **kwargs (keyword arguments)
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print("\nPerson info:")
print_info(name="Charlie", age=25, city="Boston")
```

## 4.2 Scope

- **Local Scope**: Variables inside function
- **Global Scope**: Variables at module level
- **Nonlocal Scope**: Variables in enclosing function (nested functions)
- Use `global` and `nonlocal` keywords when needed

```python
# Example: Scope

x = 10  # Global variable

def outer():
    y = 20  # Local to outer
    
    def inner():
        z = 30  # Local to inner
        print(f"Inner - x: {x}, y: {y}, z: {z}")
    
    inner()
    print(f"Outer - x: {x}, y: {y}")

outer()

# Modifying global variable
def modify_global():
    global x
    x = 100
    print(f"Modified global x: {x}")

modify_global()
print(f"Global x after function: {x}")
```

# Part 5: Object-Oriented Programming (OOP)

## 5.1 Classes and Objects

- **Class**: Blueprint for objects
- **Object**: Instance of a class
- **Attributes**: Data/properties
- **Methods**: Functions within class
- **Constructor**: `__init__` method

```python
# Example: Classes and Objects

class Car:
    # Class variable
    wheels = 4
    
    # Constructor
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year
    
    # Method
    def display_info(self):
        return f"{self.year} {self.brand} {self.model}"
    
    # Method
    def age(self, current_year=2024):
        return current_year - self.year

# Create objects
car1 = Car("Toyota", "Camry", 2020)
car2 = Car("Honda", "Civic", 2022)

print(car1.display_info())
print(f"Age: {car1.age()} years")
print(f"Wheels: {car1.wheels}")
```

## 5.2 Inheritance

- Child class inherits from parent class
- `super()` to access parent methods
- Allows code reuse and polymorphism

```python
# Example: Inheritance

class Vehicle:
    def __init__(self, brand):
        self.brand = brand
    
    def start(self):
        return f"{self.brand} is starting..."

class Bike(Vehicle):
    def __init__(self, brand, bike_type):
        super().__init__(brand)
        self.bike_type = bike_type
    
    def start(self):
        return f"{self.brand} {self.bike_type} is starting..."

# Create object
bike = Bike("Harley", "Cruiser")
print(bike.start())
print(f"Brand: {bike.brand}")
```

# Part 6: Error Handling

## 6.1 Try-Except-Finally

- `try`: Code that might raise error
- `except`: Handle specific errors
- `else`: Executed if no error
- `finally`: Always executed

## Common Exceptions
- `ValueError`: Invalid value
- `TypeError`: Wrong data type
- `KeyError`: Dictionary key not found
- `IndexError`: List index out of range
- `FileNotFoundError`: File not found
- `ZeroDivisionError`: Division by zero

```python
# Example: Error Handling

# Try-except
try:
    num = int("abc")
except ValueError:
    print("Error: Invalid value for integer conversion")
except Exception as e:
    print(f"Unexpected error: {e}")

# Try-except-else
try:
    num = int("123")
except ValueError:
    print("Error: Invalid value")
else:
    print(f"Success: Converted to {num}")

# Try-except-finally
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Error: Cannot divide by zero")
else:
    print(f"Result: {result}")
finally:
    print("Calculation completed")

# Multiple exceptions
def process_data(data):
    try:
        value = int(data)
        result = 100 / value
        return result
    except ValueError:
        return "Error: Invalid number"
    except ZeroDivisionError:
        return "Error: Cannot divide by zero"

print(f"\nProcess '0': {process_data('0')}")
print(f"Process '10': {process_data('10')}")
print(f"Process 'abc': {process_data('abc')}")
```

# Part 7: String Operations

## 7.1 String Methods

- **upper(), lower()**: Case conversion
- **strip()**: Remove whitespace
- **split()**: Split into list
- **join()**: Combine list to string
- **replace()**: Replace substring
- **find()**: Search substring
- **startswith(), endswith()**: Check start/end

```python
# Example: String Operations

text = "  Hello World  "

print(f"Original: '{text}'")
print(f"Upper: '{text.upper()}'")
print(f"Lower: '{text.lower()}'")
print(f"Strip: '{text.strip()}'")

# String splitting and joining
sentence = "Python is amazing"
words = sentence.split()
print(f"\nSplit: {words}")
print(f"Join: {'-'.join(words)}")

# String replacement
text = "I like apples. I like bananas."
new_text = text.replace("like", "love")
print(f"\nOriginal: {text}")
print(f"Replaced: {new_text}")

# String formatting
name = "Alice"
age = 30
print(f"\nF-string: My name is {name} and I'm {age}")
print("Format: My name is {} and I'm {}".format(name, age))
print(f"Formatted: My name is {name:>10} and I'm {age:0>3}")
```

# Part 8: File Handling

## 8.1 Reading and Writing Files

- `open()`: Open file
- Modes: 'r' (read), 'w' (write), 'a' (append), 'b' (binary)
- `read()`: Read entire file
- `readline()`: Read one line
- `readlines()`: Read all lines as list
- `write()`: Write to file
- `close()`: Close file
- Use `with` statement for automatic closing

```python
# Example: File Handling

# Write to file
with open("sample.txt", "w") as file:
    file.write("Hello, Python!\n")
    file.write("This is a sample file.\n")
    file.write("File handling is easy.\n")

print("File written successfully")

# Read entire file
with open("sample.txt", "r") as file:
    content = file.read()
    print(f"\nFile content:\n{content}")

# Read line by line
print("\nReading line by line:")
with open("sample.txt", "r") as file:
    for line in file:
        print(f"  {line.strip()}")

# Append to file
with open("sample.txt", "a") as file:
    file.write("This is an appended line.\n")

print("\nLine appended successfully")
```

# Part 9: Comprehensions and Generators

## 9.1 List Comprehension

- Concise way to create lists
- Syntax: `[expression for item in iterable if condition]`

## 9.2 Dictionary and Set Comprehension

- Similar syntax for dictionaries and sets

## 9.3 Generators

- Use `yield` instead of `return`
- Memory efficient for large sequences
- Lazy evaluation

```python
# Example: Comprehensions

# List comprehension
squares = [x**2 for x in range(1, 6)]
print(f"Squares: {squares}")

# With condition
even_squares = [x**2 for x in range(1, 11) if x % 2 == 0]
print(f"Even squares: {even_squares}")

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(1, 6)}
print(f"Squares dict: {squares_dict}")

# Set comprehension
unique_lengths = {len(word) for word in ["apple", "banana", "cat", "dog"]}
print(f"Unique lengths: {unique_lengths}")
```

```python
# Example: Generators

# Generator function
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

print("Generator output:")
for num in count_up_to(5):
    print(num, end=" ")
print()

# Generator expression
gen = (x**2 for x in range(5))
print(f"\nGenerator expression: {list(gen)}")
```

# Part 10: Working with Modules and Imports

## 10.1 Import Types

- `import module`: Import entire module
- `from module import name`: Import specific item
- `import module as alias`: Import with alias
- `from module import *`: Import all (avoid if possible)

## 10.2 Useful Built-in Modules

- `math`: Mathematical functions
- `random`: Random number generation
- `datetime`: Date and time
- `os`: Operating system operations
- `json`: JSON encoding/decoding
- `re`: Regular expressions

```python
# Example: Modules

import math
import random
from datetime import datetime, timedelta
import json

# Math module
print(f"Square root of 16: {math.sqrt(16)}")
print(f"Pi: {math.pi}")
print(f"Ceiling of 4.3: {math.ceil(4.3)}")

# Random module
print(f"\nRandom integer (1-10): {random.randint(1, 10)}")
print(f"Random float (0-1): {random.random()}")
print(f"Random choice: {random.choice(['apple', 'banana', 'cherry'])}")

# Datetime module
now = datetime.now()
print(f"\nCurrent date/time: {now}")
future = now + timedelta(days=7)
print(f"Date in 7 days: {future}")

# JSON module
data = {"name": "Alice", "age": 30, "city": "New York"}
json_str = json.dumps(data)
print(f"\nJSON string: {json_str}")
parsed = json.loads(json_str)
print(f"Parsed: {parsed}")
```

# Part 11: Practice Exercises

## Exercise 1: Temperature Converter
Convert Celsius to Fahrenheit and vice versa.
- Formula: F = (C * 9/5) + 32

```python
# Exercise 1 Solution

def celsius_to_fahrenheit(c):
    return (c * 9/5) + 32

def fahrenheit_to_celsius(f):
    return (f - 32) * 5/9

# Test
c_temp = 25
f_temp = celsius_to_fahrenheit(c_temp)
print(f"{c_temp}°C = {f_temp:.2f}°F")

f_temp2 = 77
c_temp2 = fahrenheit_to_celsius(f_temp2)
print(f"{f_temp2}°F = {c_temp2:.2f}°C")
```

## Exercise 2: Palindrome Checker
Check if a string is a palindrome (reads same forwards and backwards).

```python
# Exercise 2 Solution

def is_palindrome(text):
    # Remove spaces and convert to lowercase
    cleaned = text.replace(" ", "").lower()
    # Check if it equals its reverse
    return cleaned == cleaned[::-1]

# Test
words = ["racecar", "hello", "level", "A man a plan a canal Panama"]
for word in words:
    result = is_palindrome(word)
    print(f"'{word}' is palindrome: {result}")
```

## Exercise 3: List Statistics
Calculate statistics for a list (mean, median, mode).

```python
# Exercise 3 Solution

def calculate_stats(numbers):
    # Mean
    mean = sum(numbers) / len(numbers)
    
    # Median
    sorted_nums = sorted(numbers)
    n = len(sorted_nums)
    if n % 2 == 0:
        median = (sorted_nums[n//2 - 1] + sorted_nums[n//2]) / 2
    else:
        median = sorted_nums[n//2]
    
    # Mode
    frequency = {}
    for num in numbers:
        frequency[num] = frequency.get(num, 0) + 1
    mode = max(frequency, key=frequency.get)
    
    return mean, median, mode

# Test
data = [1, 2, 2, 3, 3, 3, 4, 5, 5, 6]
mean, median, mode = calculate_stats(data)
print(f"Data: {data}")
print(f"Mean: {mean:.2f}")
print(f"Median: {median}")
print(f"Mode: {mode}")
```

## Exercise 4: Grade Analyzer
Analyze student grades and provide statistics.

```python
# Exercise 4 Solution

class GradeAnalyzer:
    def __init__(self, grades_dict):
        self.grades = grades_dict
    
    def average(self):
        return sum(self.grades.values()) / len(self.grades)
    
    def highest(self):
        student = max(self.grades, key=self.grades.get)
        return student, self.grades[student]
    
    def lowest(self):
        student = min(self.grades, key=self.grades.get)
        return student, self.grades[student]
    
    def report(self):
        avg = self.average()
        highest_student, highest_grade = self.highest()
        lowest_student, lowest_grade = self.lowest()
        
        print(f"Class Average: {avg:.2f}")
        print(f"Highest: {highest_student} ({highest_grade})")
        print(f"Lowest: {lowest_student} ({lowest_grade})")

# Test
students = {
    "Alice": 92,
    "Bob": 85,
    "Charlie": 88,
    "Diana": 95,
    "Eve": 78
}

analyzer = GradeAnalyzer(students)
analyzer.report()
```

## Exercise 5: Word Frequency Counter
Count frequency of words in a text.

```python
# Exercise 5 Solution

def word_frequency(text):
    # Convert to lowercase and split
    words = text.lower().split()
    # Remove punctuation (simplified)
    words = [word.strip('.,!?;:"') for word in words]
    # Count frequency
    frequency = {}
    for word in words:
        frequency[word] = frequency.get(word, 0) + 1
    # Sort by frequency
    sorted_freq = sorted(frequency.items(), key=lambda x: x[1], reverse=True)
    return sorted_freq

# Test
text = "Python is great. Python is powerful. I love Python."
result = word_frequency(text)
print(f"Word Frequency:")
for word, count in result:
    print(f"  {word}: {count}")
```

# Key Takeaways

## Python Fundamentals
1. **Variables and Types**: Dynamically typed language
2. **Operators**: Arithmetic, comparison, logical
3. **Control Flow**: if/elif/else, for/while loops
4. **Data Structures**: Lists, tuples, dicts, sets
5. **Functions**: Reusable, parametrized code blocks
6. **OOP**: Classes, inheritance, polymorphism
7. **Error Handling**: Try-except-finally blocks
8. **File I/O**: Read/write operations
9. **Comprehensions**: Concise syntax for creating collections
10. **Modules**: Organize and reuse code

## Best Practices
- Use meaningful variable and function names
- Follow PEP 8 style guide
- Write docstrings for functions
- Use type hints for clarity
- Handle errors gracefully
- Test your code thoroughly
- Keep functions small and focused
- Use comprehensions for clarity

## Next Steps
- Practice with real-world problems
- Learn popular libraries (NumPy, Pandas, Requests)
- Build projects combining multiple concepts
- Read others' code and learn patterns
- Contribute to open-source projects

**Happy Coding! 🐍**
