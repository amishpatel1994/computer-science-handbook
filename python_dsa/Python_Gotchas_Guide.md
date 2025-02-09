# Python Gotchas and Essential Features Guide

A comprehensive guide to Python's unique features, common pitfalls, and best practices.

## 1. Mutable Default Arguments

**Description**: In Python, default arguments are evaluated when the function is defined, not when it's called. If the default value is mutable (like a list or dictionary), it will be shared across all function calls. This can lead to unexpected behavior where modifications to the default argument persist between function calls.

### The Gotcha
```python
def append_to(element, list=[]):    # DANGEROUS!
    list.append(element)
    return list

print(append_to(1))  # [1]
print(append_to(2))  # [1, 2] - Unexpected! The same list is being modified
```

### The Fix
```python
def append_to(element, list=None):
    if list is None:
        list = []    # Create a new list for each function call
    list.append(element)
    return list
```

## 2. Late Binding Closures

**Description**: Python's closures are late-binding, meaning that the values of variables used in closures are looked up at the time the inner function is called. This can lead to unexpected behavior when creating functions in loops, as all functions will bind to the same final value of the loop variable.

### The Gotcha
```python
funcs = []
for i in range(3):
    def func():
        return i    # References i from enclosing scope
    funcs.append(func)

print([f() for f in funcs])  # [2, 2, 2] - All functions reference the final value of i
```

### The Fix
```python
funcs = []
for i in range(3):
    def func(x=i):  # Bind immediately with default argument
        return x
    funcs.append(func)

print([f() for f in funcs])  # [0, 1, 2] - Each function captures its own value
```

## 3. Variable Scope Rules

**Description**: Python follows the LEGB rule for variable scope resolution. Understanding this hierarchy is crucial for avoiding naming conflicts and unexpected variable access behavior.

### The LEGB Rule
- Local (L): Names assigned in any way within a function
- Enclosing (E): Names in the enclosing function for nested functions
- Global (G): Names assigned at the module level
- Built-in (B): Names preassigned in the built-in names module

```python
x = 'global'
def outer():
    x = 'outer'
    def inner():
        # x = 'inner'  # Uncomment to see local scope
        print(x)       # Prints 'outer' due to LEGB rule
    inner()

outer()
```

## 4. Identity vs Equality

**Description**: Python's 'is' operator checks for identity (same object in memory), while '==' checks for equality (same value). Additionally, Python implements integer caching for small integers, which can lead to confusing behavior when using 'is'.

### The Gotcha
```python
a = 256
b = 256
print(a is b)      # True (due to integer caching for -5 to 256)

c = 257
d = 257
print(c is d)      # False (outside cache range)
```

### Best Practice
```python
# Use == for value comparison
print(a == b)      # True
print(c == d)      # True

# Use 'is' only for None comparison
x = None
if x is None:
    print("x is None")
```

## 5. Modifying Objects While Iterating

**Description**: Modifying a collection while iterating over it can lead to items being skipped or other unexpected behavior, as the iterator's internal state becomes inconsistent with the modified collection.

### The Gotcha
```python
# Modifying list while iterating
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)  # DANGEROUS! Will skip elements
```

### The Fix
```python
# Create new list or use list comprehension
numbers = [1, 2, 3, 4, 5]
numbers = [num for num in numbers if num % 2 != 0]

# Or use filter
numbers = list(filter(lambda x: x % 2 != 0, numbers))
```

## 6. Copy vs Deepcopy

**Description**: Python's default copy operations create shallow copies, which can lead to unexpected behavior with nested objects. Understanding the difference between shallow and deep copying is crucial for proper object duplication.

### Shallow Copy
```python
import copy

# Shallow copy only copies the first level
list1 = [[1, 2], [3, 4]]
list2 = list1.copy()  # or list2 = list1[:]
list2[0][0] = 9
print(list1)  # [[9, 2], [3, 4]] - Nested list modified!
```

### Deep Copy
```python
# Deep copy creates a completely independent copy
list1 = [[1, 2], [3, 4]]
list2 = copy.deepcopy(list1)
list2[0][0] = 9
print(list1)  # [[1, 2], [3, 4]] - Original unchanged
```

## 7. Generator Expressions vs List Comprehensions

**Description**: List comprehensions create a complete list in memory, while generator expressions create an iterator that generates values on demand. This can have significant memory implications for large datasets.

### Memory Efficiency
```python
# List comprehension (creates full list in memory)
squares = [x*x for x in range(1000000)]  # Uses more memory

# Generator expression (generates values on demand)
squares = (x*x for x in range(1000000))  # Memory efficient
```

## 8. String Formatting Options

**Description**: Python offers multiple string formatting methods, each with its own advantages. F-strings (introduced in Python 3.6) are generally the most readable and efficient option.

```python
name = "World"
age = 25

# f-strings (Python 3.6+) - Preferred: More readable and efficient
print(f"Hello, {name}! Age: {age}")

# str.format() - More verbose but supports older Python versions
print("Hello, {}! Age: {}".format(name, age))

# %-formatting (old style) - Legacy syntax, less readable
print("Hello, %s! Age: %d" % (name, age))
```

## 9. Context Managers

**Description**: Resources like files, network connections, and database connections should be properly managed to ensure they're closed after use. Context managers (with statement) handle this automatically.

### The Gotcha
```python
# Without context manager - Resource might not be properly closed
f = open('file.txt', 'w')
f.write('hello')
# f.close()  # Forgot to close!
```

### The Fix
```python
# With context manager - Automatically handles cleanup
with open('file.txt', 'w') as f:
    f.write('hello')
# File automatically closed
```

## 10. Truth Value Testing

**Description**: Python has a rich set of rules for determining truth values of objects. Understanding these rules is crucial for writing clean and correct conditional statements. Any object can be tested for truth value, with some surprising results for newcomers.

```python
# False values
bool(None)         # False
bool(False)        # False
bool(0)            # False
bool("")           # False
bool([])           # False
bool({})           # False
bool(set())        # False

# True values
bool(1)            # True
bool(-1)           # True
bool("hello")      # True
bool([1, 2])       # True
bool({'a': 1})     # True
```

## 11. Exception Handling Best Practices

**Description**: Catching all exceptions using a bare except clause is dangerous as it can mask serious errors and make debugging difficult. Always catch specific exceptions and handle them appropriately.

```python
# Bad: Catch all exceptions - masks errors and makes debugging difficult
try:
    do_something()
except:  # DANGEROUS! Catches even KeyboardInterrupt and SystemExit
    pass

# Good: Catch specific exceptions - clear and maintainable
try:
    do_something()
except ValueError as e:
    print(f"Value error: {e}")
except KeyError as e:
    print(f"Key error: {e}")
finally:
    cleanup()
```

## 12. Dictionary Merging (Python 3.5+)

**Description**: Python offers multiple ways to merge dictionaries. The newer methods using unpacking operators or the union operator are more readable and efficient than traditional methods.

```python
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 3, 'c': 4}

# Python 3.5+ using unpacking - Clean and readable
merged = {**dict1, **dict2}  # {'a': 1, 'b': 3, 'c': 4}

# Python 3.9+ using union operator - Even more concise
merged = dict1 | dict2  # {'a': 1, 'b': 3, 'c': 4}
```

## 13. Unpacking Operators

**Description**: Python's unpacking operators (* for lists/tuples and ** for dictionaries) provide powerful ways to split sequences and merge mappings. Understanding their behavior is essential for writing concise and readable code.

```python
# List unpacking - Useful for splitting sequences
first, *rest = [1, 2, 3, 4]
print(first)  # 1
print(rest)   # [2, 3, 4]

# Dictionary unpacking - Useful for combining dictionaries
dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, **dict1}  # Creates new dict with all key-value pairs
```

## 14. Property Decorators

**Description**: Properties provide a way to customize access to instance attributes, allowing you to add validation, computation, or documentation. They help maintain encapsulation while providing a clean interface.

```python
class Person:
    def __init__(self, name):
        self._name = name

    @property  # Getter method
    def name(self):
        return self._name

    @name.setter  # Setter method with validation
    def name(self, value):
        if not isinstance(value, str):
            raise TypeError("Name must be a string")
        self._name = value
```

## 15. Common Performance Pitfalls

**Description**: Certain Python operations can be unexpectedly inefficient. Understanding these performance characteristics helps in writing more efficient code.

### String Concatenation
```python
# Bad: Creates new string object each time - O(n²) complexity
result = ""
for i in range(1000):
    result += str(i)  # Inefficient string concatenation

# Good: Uses join - O(n) complexity
result = "".join(str(i) for i in range(1000))  # More efficient
```

### List Operations
```python
# Bad: insert(0) is O(n) as it shifts all elements
list1 = []
for i in range(1000):
    list1.insert(0, i)  # Inefficient, shifts all elements right

# Good: append() is O(1) and reverse() is O(n) once
list2 = []
for i in range(1000):
    list2.append(i)  # Efficient appending
list2.reverse()      # Single reverse operation
```

## 16. Debugging Tips

**Description**: Python provides several built-in debugging tools. Understanding these can significantly improve your debugging workflow and help identify issues more quickly.

```python
# Using breakpoint() (Python 3.7+) - Drops into debugger
def complex_function():
    x = 1
    breakpoint()  # Starts interactive debugging session
    y = x + 1
    return y

# Using print debugging with stderr for visibility
import sys
def debug_print(*args, **kwargs):
    print(*args, file=sys.stderr, **kwargs)  # Prints to error stream
```

## Best Practices Summary

1. Always use explicit variable names - Makes code self-documenting
2. Follow PEP 8 style guide - Ensures consistency
3. Use type hints for better code clarity (Python 3.5+) - Improves maintainability
4. Write docstrings for functions and classes - Documents behavior
5. Use context managers for resource management - Ensures cleanup
6. Handle exceptions properly - Prevents silent failures
7. Use list comprehensions judiciously - Improves readability
8. Prefer generator expressions for large datasets - Saves memory
9. Use f-strings for string formatting - More readable
10. Always close files and database connections - Prevents resource leaks
