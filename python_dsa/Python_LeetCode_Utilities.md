# Python Utilities for LeetCode

A comprehensive guide to Python utilities and built-in functions commonly used in coding interviews.

## Essential Built-in Functions

### List Operations

Lists are one of Python's most versatile and commonly used data structures. Understanding their operations and time complexities is crucial for coding interviews.

#### Basic List Operations
```python
# List creation and basic operations
arr = [1, 2, 3]
arr.append(4)      # Add to end: O(1) - Most efficient way to add elements
arr.pop()          # Remove and return last element: O(1) - Most efficient removal
arr.insert(0, 0)   # Insert at specific index: O(n) - Must shift elements
arr.remove(1)      # Remove first occurrence of value: O(n) - Must search and shift

# Length and membership testing
length = len(arr)  # Get length: O(1)
exists = 1 in arr  # Check if element exists: O(n) - Must search entire list
count = arr.count(1)  # Count occurrences: O(n) - Must scan entire list

# List slicing - Creates new list, O(k) where k is slice size
arr[start:end:step]  # start inclusive, end exclusive, step determines increment
arr[::-1]           # Reverse list: O(n) - Creates new reversed list
arr[1:]             # Everything except first element: O(k)
arr[:-1]            # Everything except last element: O(k)
arr[::2]            # Every second element: O(k)

# List comprehension - Concise way to create lists
squares = [x*x for x in range(10)]              # Basic comprehension
evens = [x for x in range(10) if x % 2 == 0]    # With condition
matrix = [[0]*3 for _ in range(3)]              # 2D list creation

# Sorting operations
arr.sort()                  # In-place sort: O(n log n) - Modifies original list
arr.sort(reverse=True)      # Descending order: O(n log n)
sorted_arr = sorted(arr)    # Returns new sorted list: O(n log n)
arr.sort(key=lambda x: len(str(x)))  # Sort with custom key function

# Advanced list operations
arr.extend([4, 5, 6])      # Add multiple elements: O(k) where k is length of iterable
arr.index(1)               # Find index of first occurrence: O(n)
arr.reverse()              # In-place reverse: O(n)
```

### String Operations

Strings in Python are immutable sequences of characters. Understanding string manipulation is essential for many coding problems.

```python
# String creation and basic operations
s = "hello"
length = len(s)            # Get length: O(1)
char = s[0]               # Access character: O(1)
substring = s[1:4]        # Slicing: O(k) where k is substring length

# String methods
upper_s = s.upper()       # Convert to uppercase: O(n)
lower_s = s.lower()       # Convert to lowercase: O(n)
cap_s = s.capitalize()    # Capitalize first letter: O(n)

# String searching
index = s.find('l')       # Find first occurrence: O(n)
last_index = s.rfind('l') # Find last occurrence: O(n)
count = s.count('l')      # Count occurrences: O(n)

# String checking
is_alpha = s.isalpha()    # Check if all alphabetic: O(n)
is_digit = s.isdigit()    # Check if all digits: O(n)
is_alnum = s.isalnum()    # Check if alphanumeric: O(n)

# String splitting and joining
words = s.split()         # Split by whitespace: O(n)
words = s.split(',')      # Split by delimiter: O(n)
joined = ' '.join(words)  # Join with delimiter: O(n)

# String formatting
f_string = f"Value is {length}"    # f-strings (Python 3.6+)
formatted = "Value is {}".format(length)  # str.format()
old_style = "Value is %d" % length        # %-formatting

# String stripping
stripped = s.strip()      # Remove leading/trailing whitespace: O(n)
lstrip = s.lstrip()      # Remove leading whitespace: O(n)
rstrip = s.rstrip()      # Remove trailing whitespace: O(n)

# String replacement
new_s = s.replace('l', 'L')  # Replace all occurrences: O(n)
```

### Dictionary Operations

Dictionaries are hash-based data structures providing fast key-value pair operations.

```python
# Dictionary creation and basic operations
d = {'a': 1, 'b': 2}
d['c'] = 3               # Add/update key-value pair: O(1) average
value = d['a']           # Access value by key: O(1) average
value = d.get('a', 0)    # Access with default value: O(1) average
del d['a']               # Remove key-value pair: O(1) average

# Dictionary methods
keys = d.keys()          # Get view of keys: O(1)
values = d.values()      # Get view of values: O(1)
items = d.items()        # Get view of key-value pairs: O(1)

# Dictionary membership
exists = 'a' in d        # Check key existence: O(1) average
value = d.pop('a', None) # Remove and return value with default: O(1) average

# Dictionary comprehension
squares = {x: x*x for x in range(5)}  # Create dictionary with comprehension

# Dictionary merging (Python 3.5+)
d1 = {'a': 1, 'b': 2}
d2 = {'c': 3, 'd': 4}
merged = {**d1, **d2}    # Merge dictionaries: O(n)

# Default dictionary
from collections import defaultdict
d = defaultdict(list)    # Create dictionary with default value type
d['key'].append(1)       # No KeyError if key doesn't exist
```

### Set Operations

Sets are unordered collections of unique elements, perfect for membership testing and removing duplicates.

```python
# Set creation and basic operations
s = {1, 2, 3}           # Create set directly
s = set([1, 2, 2, 3])   # Create from iterable (removes duplicates)
s.add(4)                # Add element: O(1) average
s.remove(4)             # Remove element: O(1) average
s.discard(4)            # Remove if exists: O(1) average

# Set operations
s1 = {1, 2, 3}
s2 = {3, 4, 5}
union = s1 | s2         # Union: O(len(s1) + len(s2))
inter = s1 & s2         # Intersection: O(min(len(s1), len(s2)))
diff = s1 - s2          # Difference: O(len(s1))
sym_diff = s1 ^ s2      # Symmetric difference: O(len(s1) + len(s2))

# Set membership
exists = 1 in s         # Check membership: O(1) average

# Set comprehension
evens = {x for x in range(10) if x % 2 == 0}  # Create set with comprehension
```

### Heap Operations

Heaps are binary trees that maintain the heap property, useful for priority queues and finding k-th elements.

```python
import heapq

# Heap creation and basic operations
arr = [3, 1, 4, 1, 5]
heapq.heapify(arr)      # Convert list to heap in-place: O(n)
heapq.heappush(arr, 2)  # Add element: O(log n)
min_val = heapq.heappop(arr)  # Remove and return smallest: O(log n)

# Advanced heap operations
largest = heapq.nlargest(3, arr)  # Get k largest elements: O(n log k)
smallest = heapq.nsmallest(3, arr)  # Get k smallest elements: O(n log k)

# Custom objects in heap
class Item:
    def __init__(self, name, priority):
        self.name = name
        self.priority = priority
    
    def __lt__(self, other):
        return self.priority < other.priority

heap = []
heapq.heappush(heap, Item('task1', 1))  # Custom comparison using __lt__
```

## Collections Module

The `collections` module provides specialized container datatypes as alternatives to Python's general-purpose built-in containers. Here are the most commonly used ones in coding interviews:

### Counter
```python
from collections import Counter

# Creating Counters
counter = Counter(['a', 'a', 'b', 'b', 'b'])  # From iterable
counter = Counter({'a': 2, 'b': 3})           # From dictionary
counter = Counter(a=2, b=3)                   # From keyword args

# Common operations
most_common = counter.most_common(2)          # Get 2 most common elements: [('b', 3), ('a', 2)]
counter['a']                                  # Get count: 2
counter['c']                                  # Get count of missing: 0 (no KeyError)

# Arithmetic operations
c1 = Counter(['a', 'b', 'b'])
c2 = Counter(['b', 'c'])
print(c1 + c2)                               # Add counts: Counter({'b': 3, 'a': 1, 'c': 1})
print(c1 - c2)                               # Subtract counts: Counter({'a': 1, 'b': 1})
print(c1 & c2)                               # Intersection: Counter({'b': 1})
print(c1 | c2)                               # Union: Counter({'b': 2, 'a': 1, 'c': 1})

# Common patterns
# 1. Finding most common elements
text = "hello world"
char_count = Counter(text).most_common()      # [('l', 3), ('o', 2), ...]

# 2. Finding anagrams
def are_anagrams(s1, s2):
    return Counter(s1) == Counter(s2)

# 3. Finding elements above threshold
counter = Counter([1,1,2,2,2,3])
[k for k, v in counter.items() if v > 1]      # Elements occurring more than once
```

### defaultdict
```python
from collections import defaultdict

# Different default factories
d1 = defaultdict(list)      # Default value: empty list
d2 = defaultdict(int)       # Default value: 0
d3 = defaultdict(set)       # Default value: empty set
d4 = defaultdict(lambda: 5) # Default value: 5

# Common patterns
# 1. Grouping elements
words = ['eat', 'tea', 'tan', 'ate', 'nat', 'bat']
anagrams = defaultdict(list)
for word in words:
    sorted_word = ''.join(sorted(word))
    anagrams[sorted_word].append(word)
# Result: {'aet': ['eat', 'tea', 'ate'], 'ant': ['tan', 'nat'], 'abt': ['bat']}

# 2. Counting with automatic initialization
numbers = [1, 2, 2, 3, 3, 3]
counts = defaultdict(int)
for num in numbers:
    counts[num] += 1
# Result: {1: 1, 2: 2, 3: 3}

# 3. Building graph adjacency lists
graph = defaultdict(list)
edges = [(1,2), (1,3), (2,3)]
for u, v in edges:
    graph[u].append(v)
    graph[v].append(u)  # For undirected graph
```

### deque (Double-ended Queue)
```python
from collections import deque

# Creation
d = deque()                 # Empty deque
d = deque([1, 2, 3])       # From iterable
d = deque(maxlen=3)        # Fixed-size deque

# Basic operations
d.append(4)                 # Add to right: O(1)
d.appendleft(0)            # Add to left: O(1)
d.pop()                    # Remove from right: O(1)
d.popleft()               # Remove from left: O(1)
d.extend([4, 5, 6])       # Extend on right: O(k)
d.extendleft([3, 2, 1])   # Extend on left: O(k)

# Other operations
d.rotate(1)                # Rotate right by 1
d.rotate(-1)               # Rotate left by 1
d.clear()                  # Remove all elements
len(d)                     # Get length

# Common patterns
# 1. Sliding window
def max_sliding_window(nums, k):
    d = deque()
    result = []
    for i, num in enumerate(nums):
        # Remove elements outside window
        while d and d[0] < i - k + 1:
            d.popleft()
        # Remove smaller elements
        while d and nums[d[-1]] < num:
            d.pop()
        d.append(i)
        if i >= k - 1:
            result.append(nums[d[0]])
    return result

# 2. BFS implementation
def bfs(graph, start):
    visited = {start}
    queue = deque([start])
    while queue:
        vertex = queue.popleft()
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

## Heapq Module
```python
import heapq

# Creation
heap = []
heapq.heapify(heap)        # Convert list to heap in-place: O(n)

# Basic operations
heapq.heappush(heap, 1)    # Add element: O(log n)
min_val = heapq.heappop(heap)  # Remove & return smallest: O(log n)
min_val = heap[0]          # Peek at smallest: O(1)

# Advanced operations
largest = heapq.nlargest(3, heap)    # Get 3 largest elements: O(n log k)
smallest = heapq.nsmallest(3, heap)  # Get 3 smallest elements: O(n log k)
heapq.heappushpop(heap, 2)           # Push then pop: O(log n)
heapq.heapreplace(heap, 2)           # Pop then push: O(log n)

# Common patterns
# 1. Priority Queue with custom objects
class Task:
    def __init__(self, priority, description):
        self.priority = priority
        self.description = description
    
    def __lt__(self, other):
        return self.priority < other.priority

# Usage
tasks = []
heapq.heappush(tasks, Task(3, "Low priority"))
heapq.heappush(tasks, Task(1, "High priority"))

# 2. K-th largest element
def find_kth_largest(nums, k):
    heap = []
    for num in nums:
        heapq.heappush(heap, num)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]

# 3. Merge K sorted lists
def merge_k_sorted(lists):
    heap = []
    result = []
    
    # Add first element from each list
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))
    
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        
        if elem_idx + 1 < len(lists[list_idx]):
            next_elem = lists[list_idx][elem_idx + 1]
            heapq.heappush(heap, (next_elem, list_idx, elem_idx + 1))
    
    return result
```

## Itertools Module
```python
from itertools import (
    combinations, combinations_with_replacement,
    permutations, product, chain,
    count, cycle, repeat,
    accumulate, groupby
)

# Combinations
comb = list(combinations('ABC', 2))       # [('A','B'), ('A','C'), ('B','C')]
comb_r = list(combinations_with_replacement('ABC', 2))  # Include repeated elements

# Permutations
perm = list(permutations('ABC', 2))      # All 2-length permutations

# Cartesian Product
prod = list(product('AB', '12'))         # [('A','1'), ('A','2'), ('B','1'), ('B','2')]
prod_repeat = list(product('AB', repeat=2))  # [('A','A'), ('A','B'), ('B','A'), ('B','B')]

# Infinite iterators
counter = count(10, 2)                    # Count from 10 by 2: 10, 12, 14, ...
cycler = cycle('ABC')                     # Cycle through: A, B, C, A, B, C, ...
repeater = repeat(10, 3)                  # Repeat 10 three times

# Chain iterables
combined = chain('ABC', '123')            # Combine iterables: A, B, C, 1, 2, 3

# Accumulate (running sum)
nums = [1, 2, 3, 4]
acc = list(accumulate(nums))              # [1, 3, 6, 10]
acc_mult = list(accumulate(nums, lambda x, y: x * y))  # [1, 2, 6, 24]

# Group consecutive elements
data = ['A', 'A', 'B', 'B', 'B', 'C']
groups = groupby(data)                    # Group consecutive same elements

# Common patterns
# 1. Generate all possible subsets
def get_all_subsets(elements):
    return chain.from_iterable(
        combinations(elements, r) 
        for r in range(len(elements) + 1)
    )

# 2. Generate sliding windows
def sliding_window(seq, n):
    it = iter(seq)
    result = tuple(islice(it, n))
    if len(result) == n:
        yield result    
    for elem in it:
        result = result[1:] + (elem,)
        yield result

# 3. Find all possible paths in a grid
def grid_paths(m, n):
    return product(range(m), range(n))
```

## Math and Number Operations
```python
import math
from decimal import Decimal, getcontext
from fractions import Fraction

# Constants
math.pi                    # π (3.141592...)
math.e                     # e (2.718281...)
float('inf')              # Infinity
float('-inf')             # Negative infinity

# Basic operations
abs(-5)                   # Absolute value: 5
pow(2, 3)                 # Power: 8
math.sqrt(16)             # Square root: 4
math.ceil(3.7)            # Ceiling: 4
math.floor(3.7)           # Floor: 3
round(3.7)                # Round: 4
divmod(7, 3)              # (quotient, remainder): (2, 1)

# Trigonometry
math.sin(math.pi/2)       # Sine
math.cos(math.pi)         # Cosine
math.tan(math.pi/4)       # Tangent
math.degrees(math.pi)     # Convert radians to degrees
math.radians(180)         # Convert degrees to radians

# Logarithms
math.log(8, 2)            # Log base 2: 3
math.log10(100)           # Log base 10: 2
math.log2(8)              # Log base 2: 3
math.log1p(x)             # log(1 + x)

# GCD and LCM
math.gcd(12, 18)          # Greatest Common Divisor: 6
def lcm(a, b):            # Least Common Multiple
    return abs(a * b) // math.gcd(a, b)

# Binary operations
bin(10)                   # Convert to binary string: '0b1010'
format(10, 'b')          # Binary without prefix: '1010'
x & y                     # Bitwise AND
x | y                     # Bitwise OR
x ^ y                     # Bitwise XOR
x << y                    # Left shift
x >> y                    # Right shift
~x                        # Bitwise NOT

# Precise decimal arithmetic
getcontext().prec = 28    # Set precision
Decimal('0.1') + Decimal('0.2')  # Exact: Decimal('0.3')

# Fraction arithmetic
Fraction(1, 3) + Fraction(1, 6)  # Exact: Fraction(1, 2)

# Common patterns
# 1. Check if number is prime
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True

# 2. Generate prime numbers (Sieve of Eratosthenes)
def sieve(n):
    primes = [True] * (n + 1)
    primes[0] = primes[1] = False
    for i in range(2, int(math.sqrt(n)) + 1):
        if primes[i]:
            for j in range(i * i, n + 1, i):
                primes[j] = False
    return [i for i in range(n + 1) if primes[i]]

# 3. Fast exponentiation
def power(base, exp, mod=None):
    result = 1
    while exp > 0:
        if exp & 1:
            result = result * base if mod is None else (result * base) % mod
        base = base * base if mod is None else (base * base) % mod
        exp >>= 1
    return result
```

## Time Complexity Reference

### List Operations
- Append: O(1)
- Pop last: O(1)
- Pop intermediate: O(n)
- Insert: O(n)
- Get item: O(1)
- Set item: O(1)
- Delete item: O(n)
- Slice: O(k)
- Extend: O(k)
- Sort: O(n log n)

### Dict Operations
- Get item: O(1)
- Set item: O(1)
- Delete item: O(1)
- Containment: O(1)

### Set Operations
- Add: O(1)
- Remove: O(1)
- Containment: O(1)
- Union/Intersection: O(min(len(s), len(t)))

## Common LeetCode Patterns

### 1. Two Pointers Pattern

Two pointers is an extremely common pattern for solving array problems. It involves having two integer variables that both traverse through the array (or linked list) in some way. The exact movement depends on the problem.

#### When to use:
- Searching for pairs in a sorted array
- Finding longest/shortest subarray meeting some condition
- Finding palindromes
- Merging two sorted arrays
- Reversing arrays

#### Template Code:
```python
def two_pointers_from_ends(arr):
    left = 0
    right = len(arr) - 1
    
    while left < right:
        # Process elements from both ends
        current_sum = arr[left] + arr[right]
        
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1  # Need larger values
        else:
            right -= 1  # Need smaller values
    
    return []  # No solution found

def two_pointers_same_direction(arr):
    slow = fast = 0
    
    while fast < len(arr):
        # Process current window
        # Update slow pointer based on condition
        if condition:
            slow += 1
        # Always move fast pointer
        fast += 1
    
    return result
```

#### Example Problems:
1. Two Sum II (sorted array)
2. Container With Most Water
3. Remove Duplicates from Sorted Array
4. Valid Palindrome

### 2. Sliding Window Pattern

The sliding window pattern is used to perform operations on a specific window size of an array or linked list. The window can be fixed or variable size.

#### When to use:
- Finding subarrays that meet certain conditions
- Calculating running averages
- Finding longest/shortest substring with certain properties
- Maximum sum subarray of size k

#### Template Code:
```python
def sliding_window_fixed(arr, k):
    # Initialize window sums and result
    window_sum = sum(arr[:k])
    max_sum = window_sum
    
    # Slide window
    for i in range(k, len(arr)):
        # Remove first element of previous window
        # Add last element of current window
        window_sum = window_sum - arr[i-k] + arr[i]
        max_sum = max(max_sum, window_sum)
    
    return max_sum

def sliding_window_variable(s):
    window_start = 0
    max_length = 0
    window_counts = {}  # or any other window property
    
    for window_end in range(len(s)):
        # Add the next element to window
        window_counts[s[window_end]] = window_counts.get(s[window_end], 0) + 1
        
        # Shrink window if condition is violated
        while window_condition_broken():
            # Remove first element of window
            window_counts[s[window_start]] -= 1
            if window_counts[s[window_start]] == 0:
                del window_counts[s[window_start]]
            window_start += 1
        
        # Update result
        max_length = max(max_length, window_end - window_start + 1)
    
    return max_length
```

#### Example Problems:
1. Maximum Sum Subarray of Size K
2. Longest Substring Without Repeating Characters
3. Minimum Window Substring
4. Permutation in String

### 3. Fast and Slow Pointers (Floyd's Cycle Detection)

This pattern uses two pointers moving at different speeds. Extremely useful for cycle detection or finding middle elements.

#### When to use:
- Detecting cycles in linked lists
- Finding middle element of linked list
- Finding nth element from end
- Determining if linked list is palindrome

#### Template Code:
```python
def has_cycle(head):
    if not head or not head.next:
        return False
    
    slow = head
    fast = head.next
    
    while slow != fast:
        if not fast or not fast.next:
            return False
        slow = slow.next
        fast = fast.next.next
    
    return True

def find_cycle_start(head):
    if not head or not head.next:
        return None
    
    # Find meeting point
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            break
    else:
        return None
    
    # Find cycle start
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next
    
    return slow
```

#### Example Problems:
1. Linked List Cycle
2. Find Cycle Start
3. Middle of Linked List
4. Palindrome Linked List

### 4. Merge Intervals Pattern

This pattern deals with overlapping intervals or ranges.

#### When to use:
- Finding overlapping intervals
- Merging intervals
- Finding meeting times
- Scheduling problems

#### Template Code:
```python
def merge_intervals(intervals):
    if not intervals:
        return []
    
    # Sort by start time
    intervals.sort(key=lambda x: x[0])
    
    merged = [intervals[0]]
    
    for interval in intervals[1:]:
        last_end = merged[-1][1]
        current_start = interval[0]
        current_end = interval[1]
        
        # If overlapping, merge
        if current_start <= last_end:
            merged[-1][1] = max(last_end, current_end)
        else:
            merged.append(interval)
    
    return merged
```

#### Example Problems:
1. Merge Intervals
2. Insert Interval
3. Non-overlapping Intervals
4. Meeting Rooms II

### 5. Binary Search Pattern

Binary search is not just for sorted arrays! It can be used whenever you can eliminate half the search space.

#### When to use:
- Searching in sorted array
- Finding first/last occurrence
- Finding peak element
- Finding minimum in rotated array
- Finding answer when you can guess solution space

#### Template Code:
```python
def binary_search_basic(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1

def binary_search_leftmost(arr, target):
    left, right = 0, len(arr)
    
    while left < right:
        mid = left + (right - left) // 2
        if arr[mid] < target:
            left = mid + 1
        else:
            right = mid
    
    return left if left < len(arr) and arr[left] == target else -1

def binary_search_answer_space(arr, condition):
    left, right = min(arr), max(arr)
    
    while left < right:
        mid = left + (right - left) // 2
        if condition(mid):
            right = mid
        else:
            left = mid + 1
    
    return left
```

#### Example Problems:
1. Binary Search
2. First Bad Version
3. Find Minimum in Rotated Sorted Array
4. Search in Rotated Sorted Array

### 6. DFS (Depth-First Search) Pattern

DFS is crucial for tree and graph traversal problems. It's often implemented recursively.

#### When to use:
- Tree traversal
- Path finding
- Graph exploration
- Combination/permutation problems
- Backtracking problems

#### Template Code:
```python
# Tree DFS
def dfs_tree(root):
    if not root:
        return
    
    # Process current node
    process_node(root)
    
    # Recurse on children
    dfs_tree(root.left)
    dfs_tree(root.right)

# Graph DFS with visited set
def dfs_graph(graph, start, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(start)
    
    # Process current node
    process_node(start)
    
    # Recurse on neighbors
    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs_graph(graph, neighbor, visited)

# Backtracking template
def backtrack(candidates, path, results):
    if is_solution(path):
        results.append(path[:])
        return
    
    for candidate in candidates:
        if is_valid(candidate):
            # Make choice
            path.append(candidate)
            
            # Recurse
            backtrack(candidates, path, results)
            
            # Undo choice
            path.pop()
```

#### Example Problems:
1. Binary Tree Inorder Traversal
2. Path Sum
3. Course Schedule
4. Number of Islands

### 7. BFS (Breadth-First Search) Pattern

BFS is excellent for finding shortest paths and level-order traversals.

#### When to use:
- Level-order traversal
- Shortest path in unweighted graph
- Connected components
- Graph validation

#### Template Code:
```python
from collections import deque

def bfs_tree(root):
    if not root:
        return []
    
    result = []
    queue = deque([root])
    
    while queue:
        level_size = len(queue)
        current_level = []
        
        for _ in range(level_size):
            node = queue.popleft()
            current_level.append(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(current_level)
    
    return result

def bfs_graph(graph, start):
    visited = {start}
    queue = deque([start])
    result = []
    
    while queue:
        node = queue.popleft()
        result.append(node)
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

#### Example Problems:
1. Binary Tree Level Order Traversal
2. Word Ladder
3. Rotting Oranges
4. Perfect Squares

### 8. Dynamic Programming Pattern

DP problems can often be solved using one of several patterns.

#### When to use:
- Optimization problems
- Counting problems
- Can current problem be broken into subproblems?
- Is there overlapping between subproblems?

#### Template Code:
```python
# 1D DP
def dp_1d(n):
    dp = [0] * (n + 1)
    dp[0] = base_case
    
    for i in range(1, n + 1):
        dp[i] = some_function(dp[i-1])
    
    return dp[n]

# 2D DP
def dp_2d(m, n):
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    # Initialize base cases
    for i in range(m + 1):
        dp[i][0] = base_case1
    for j in range(n + 1):
        dp[0][j] = base_case2
    
    # Fill DP table
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            dp[i][j] = some_function(dp[i-1][j], dp[i][j-1])
    
    return dp[m][n]

# State machine DP
def state_machine_dp(arr):
    state1, state2 = init_states()
    
    for num in arr:
        next_state1 = max(state1, some_function1(state2, num))
        next_state2 = max(state2, some_function2(state1, num))
        state1, state2 = next_state1, next_state2
    
    return max(state1, state2)
```

#### Example Problems:
1. Climbing Stairs
2. Coin Change
3. Longest Increasing Subsequence
4. Edit Distance

### 9. Monotonic Stack/Queue Pattern

This pattern maintains a monotonic (increasing or decreasing) stack/queue to solve problems involving finding next/previous greater/smaller elements.

#### When to use:
- Finding next greater/smaller element
- Finding temperature spans
- Finding histogram areas
- Finding valid parentheses strings

#### Template Code:
```python
def next_greater_element(arr):
    n = len(arr)
    result = [-1] * n  # Default to -1 for no next greater element
    stack = []  # Stack will store indices
    
    for i in range(n):
        # While stack has elements and current element is greater
        # than element at stack's top index
        while stack and arr[i] > arr[stack[-1]]:
            prev_index = stack.pop()
            result[prev_index] = arr[i]
        stack.append(i)
    
    return result

def largest_rectangle_histogram(heights):
    stack = []  # Stack of (index, height)
    max_area = 0
    
    for i, h in enumerate(heights + [0]):  # Add 0 to handle remaining stack
        start = i
        while stack and stack[-1][1] > h:
            index, height = stack.pop()
            width = i - index
            max_area = max(max_area, height * width)
            start = index
        stack.append((start, h))
    
    return max_area
```

#### Example Problems:
1. Next Greater Element I
2. Daily Temperatures
3. Largest Rectangle in Histogram
4. Remove K Digits

### 10. Bit Manipulation Pattern

Bit manipulation can be used to solve various problems efficiently.

#### When to use:
- Working with binary numbers
- Optimizing space usage
- Finding unique elements
- Power of two problems

#### Template Code:
```python
def count_bits(n):
    count = 0
    while n:
        count += n & 1  # Check last bit
        n >>= 1        # Right shift
    return count

def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0

def get_bit(num, i):
    return (num & (1 << i)) != 0

def set_bit(num, i):
    return num | (1 << i)

def clear_bit(num, i):
    mask = ~(1 << i)
    return num & mask

def update_bit(num, i, value):
    mask = ~(1 << i)
    return (num & mask) | (value << i)
```

#### Example Problems:
1. Single Number
2. Number of 1 Bits
3. Missing Number
4. Power of Two

### 11. Matrix Traversal Pattern

This pattern is used for solving problems that involve 2D arrays/matrices. It's particularly useful for:
- Grid-based pathfinding problems
- Island counting and connected components
- Game board state analysis
- Image processing operations
- Flood fill algorithms
- Maze solving problems

#### When to use:
- When you need to explore or modify a 2D grid in a systematic way
- Problems involving finding connected regions or components
- When you need to process pixels in an image
- Game scenarios like chess, tic-tac-toe, or minesweeper
- Problems requiring exploration of neighboring cells
- Maze or path-finding problems

#### Key Concepts:
1. Directions Array: Used to define valid moves (usually 4 or 8 directions)
2. Boundary Checking: Ensure moves stay within grid bounds
3. Visited Set/Matrix: Track explored cells to avoid cycles
4. BFS vs DFS: Choose based on problem requirements
   - BFS: Better for shortest path problems
   - DFS: Better for exploring all possible paths

#### Template Code:
```python
def matrix_dfs(matrix, row, col, visited=None):
    if visited is None:
        visited = set()
    
    # Matrix dimensions
    rows, cols = len(matrix), len(matrix[0])
    
    # Define 4 directions: right, down, left, up
    directions = [(0,1), (1,0), (0,-1), (-1,0)]
    
    def is_valid(r, c):
        """Check if cell is within bounds and meets problem constraints."""
        return (0 <= r < rows and 
                0 <= c < cols and 
                (r, c) not in visited and
                matrix[r][c] == 1)  # Example constraint
    
    def dfs(r, c):
        """Recursive DFS implementation."""
        # Base case: invalid cell
        if not is_valid(r, c):
            return
        
        # Mark as visited
        visited.add((r, c))
        
        # Process current cell
        # ... problem-specific logic here ...
        
        # Explore all valid neighbors
        for dr, dc in directions:
            next_r, next_c = r + dr, c + dc
            dfs(next_r, next_c)
    
    # Start DFS from given position
    dfs(row, col)
    return visited

# BFS version for shortest path problems
from collections import deque

def matrix_bfs(matrix, start_row, start_col):
    rows, cols = len(matrix), len(matrix[0])
    visited = set([(start_row, start_col)])
    queue = deque([(start_row, start_col, 0)])  # (row, col, distance)
    directions = [(0,1), (1,0), (0,-1), (-1,0)]
    
    while queue:
        row, col, dist = queue.popleft()
        
        # Process current cell
        # ... problem-specific logic here ...
        
        # Explore neighbors
        for dr, dc in directions:
            next_r, next_c = row + dr, col + dc
            if (0 <= next_r < rows and 
                0 <= next_c < cols and 
                (next_r, next_c) not in visited and
                matrix[next_r][next_c] == 1):  # Example constraint
                
                visited.add((next_r, next_c))
                queue.append((next_r, next_c, dist + 1))
    
    return visited

# Example usage for Number of Islands problem
def numIslands(grid):
    if not grid:
        return 0
    
    rows, cols = len(grid), len(grid[0])
    visited = set()
    islands = 0
    
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == '1' and (r, c) not in visited:
                matrix_dfs(grid, r, c, visited)
                islands += 1
    
    return islands

# Example usage for Shortest Path in Binary Matrix
def shortestPathBinaryMatrix(grid):
    if grid[0][0] == 1:
        return -1
    
    n = len(grid)
    if n == 1:
        return 1
    
    # Include diagonal directions
    directions = [(0,1), (1,0), (0,-1), (-1,0),
                 (1,1), (1,-1), (-1,1), (-1,-1)]
    
    queue = deque([(0, 0, 1)])  # (row, col, path_length)
    visited = {(0, 0)}
    
    while queue:
        row, col, path_len = queue.popleft()
        
        for dr, dc in directions:
            next_r, next_c = row + dr, col + dc
            
            if (next_r == n-1 and next_c == n-1 and 
                grid[next_r][next_c] == 0):
                return path_len + 1
            
            if (0 <= next_r < n and 0 <= next_c < n and 
                grid[next_r][next_c] == 0 and 
                (next_r, next_c) not in visited):
                visited.add((next_r, next_c))
                queue.append((next_r, next_c, path_len + 1))
    
    return -1
```

#### Common Applications:

1. **Island Problems**
   - Count number of islands
   - Find largest island
   - Island perimeter

2. **Path Finding**
   - Shortest path in maze
   - All possible paths
   - Path with constraints

3. **Connected Components**
   - Find all connected regions
   - Count size of regions
   - Flood fill

4. **Game Board Problems**
   - Valid moves
   - Game state analysis
   - Territory calculation

5. **Image Processing**
   - Region coloring
   - Boundary detection
   - Connected pixel analysis

#### Time/Space Complexity:
- Time: O(rows × cols) - need to visit each cell
- Space: O(rows × cols) - for visited set/recursion stack
- BFS Space: O(min(rows, cols)) - queue size
- DFS Space: O(rows × cols) - recursion stack

### 12. State Machine Pattern

The State Machine Pattern is a powerful approach for problems that can be modeled as a series of states and transitions between them. This pattern is particularly useful when:
- The problem involves distinct states that an entity can be in
- There are well-defined rules for transitioning between states
- You need to track the optimal value/path through different states
- The problem involves processing sequences with specific rules

#### When to use:
- Stock trading problems with constraints (like cooldown or transaction limits)
- String parsing with specific rules or patterns
- Game scenarios with different states (e.g., player states, game phases)
- Regular expression matching
- Problems involving alternating actions or choices
- Scenarios with state-dependent decisions

#### Key Concepts:
1. States: Clear definition of possible states in the problem
2. Transitions: Rules for moving between states
3. State Variables: Variables to track current state
4. Optimal Substructure: Often combined with DP for optimization
5. State History: Sometimes needed to make decisions

#### Template Code:
```python
# Basic State Machine
def basic_state_machine(sequence):
    # Define possible states
    IDLE = 0
    PROCESSING = 1
    DONE = 2
    
    current_state = IDLE
    result = []
    
    for item in sequence:
        if current_state == IDLE:
            if is_valid_start(item):
                current_state = PROCESSING
                result.append(item)
        elif current_state == PROCESSING:
            if is_end_condition(item):
                current_state = DONE
            else:
                result.append(item)
        elif current_state == DONE:
            break
    
    return result

# State Machine with Dynamic Programming
def state_machine_dp(prices):
    """
    Example: Stock Trading with Cooldown
    States:
    - can_buy: Can buy stock today
    - can_sell: Holding stock, can sell
    - cooldown: Just sold stock, must wait
    """
    if not prices:
        return 0
    
    n = len(prices)
    
    # Initialize DP arrays for each state
    can_buy = [0] * n   # Maximum profit when we can buy
    can_sell = [0] * n  # Maximum profit when we can sell
    cooldown = [0] * n  # Maximum profit when in cooldown
    
    # Initial states
    can_sell[0] = -prices[0]  # Buy first stock
    
    # Fill DP arrays
    for i in range(1, n):
        # If we can buy, either keep waiting or buy stock
        can_buy[i] = max(can_buy[i-1], cooldown[i-1])
        
        # If we can sell, either keep holding or sell stock
        can_sell[i] = max(can_sell[i-1], can_buy[i-1] - prices[i])
        
        # Cooldown only comes after selling
        cooldown[i] = can_sell[i-1] + prices[i]
    
    # Return maximum of final states
    return max(can_buy[-1], cooldown[-1])

# Example: Regular Expression Matching
def is_match(text: str, pattern: str) -> bool:
    """
    Implement regular expression matching with support for '.' and '*'
    '.' matches any single character
    '*' matches zero or more of the preceding element
    """
    m, n = len(text), len(pattern)
    dp = [[False] * (n + 1) for _ in range(m + 1)]
    dp[0][0] = True
    
    # Handle patterns like a*, a*b*, etc.
    for j in range(2, n + 1):
        if pattern[j-1] == '*':
            dp[0][j] = dp[0][j-2]
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if pattern[j-1] == '.' or pattern[j-1] == text[i-1]:
                dp[i][j] = dp[i-1][j-1]
            elif pattern[j-1] == '*':
                dp[i][j] = dp[i][j-2]  # Zero occurrence
                if pattern[j-2] == '.' or pattern[j-2] == text[i-1]:
                    dp[i][j] = dp[i][j] or dp[i-1][j]  # One or more occurrences
    
    return dp[m][n]
```

#### Common Applications:

1. **Stock Trading Problems**
   - Buy/sell with cooldown
   - Limited transactions
   - Transaction fees
   - Multiple stocks

2. **String Processing**
   - Regular expression matching
   - State-based parsing
   - Pattern validation
   - Token processing

3. **Game Logic**
   - Player state management
   - Game phase transitions
   - Turn-based logic
   - Achievement systems

4. **Resource Management**
   - Resource allocation states
   - Process scheduling
   - State-based permissions
   - Workflow management

#### Time/Space Complexity Analysis:
- Time: O(n × s), where n is input size and s is number of states
- Space: O(n × s) for DP-based solutions
- Space: O(1) for simple state tracking
- Additional space might be needed for state history

#### Common Pitfalls and Tips:
1. Clearly define all possible states
2. Ensure all state transitions are handled
3. Consider edge cases for each state
4. Watch for invalid state transitions
5. Consider using enums for state definitions
6. Document state transition rules
7. Test all possible state combinations

### 13. Prefix Sum Pattern

The Prefix Sum Pattern is a preprocessing technique that calculates cumulative sums of array elements, enabling efficient range sum queries and transformations. This pattern is particularly powerful because it transforms range sum queries from O(n) to O(1) time complexity after preprocessing.

#### When to use:
- Computing sums of subarrays efficiently
- Finding continuous subarrays with target sum
- Calculating running averages or moving sums
- Problems involving cumulative data
- Range queries on immutable arrays
- Problems requiring difference arrays
- Finding equilibrium points in arrays

#### Key Concepts:
1. Prefix Sum Array: Contains cumulative sums up to each index
2. Range Sum: Calculated as prefixSum[right] - prefixSum[left-1]
3. 2D Prefix Sum: Used for matrix region sums
4. Difference Array: Inverse operation of prefix sum
5. Running Sum: Special case where you need all prefix sums

#### Template Code:
```python
# 1D Prefix Sum
def build_prefix_sum(arr):
    """Build prefix sum array for 1D array."""
    n = len(arr)
    prefix = [0] * (n + 1)  # One extra space for easier range sum calculation
    
    for i in range(n):
        prefix[i + 1] = prefix[i] + arr[i]
    
    return prefix

def get_range_sum(prefix, left, right):
    """Get sum of elements from index left to right (inclusive)."""
    return prefix[right + 1] - prefix[left]

# 2D Prefix Sum
def build_2d_prefix_sum(matrix):
    """Build prefix sum matrix for 2D array."""
    if not matrix or not matrix[0]:
        return []
    
    rows, cols = len(matrix), len(matrix[0])
    prefix = [[0] * (cols + 1) for _ in range(rows + 1)]
    
    for i in range(rows):
        for j in range(cols):
            prefix[i + 1][j + 1] = (
                prefix[i + 1][j] +      # Left sum
                prefix[i][j + 1] -      # Up sum
                prefix[i][j] +          # Remove double-counted region
                matrix[i][j]            # Add current cell
            )
    
    return prefix

def get_region_sum(prefix, row1, col1, row2, col2):
    """Get sum of elements in rectangle [(row1,col1), (row2,col2)]."""
    return (
        prefix[row2 + 1][col2 + 1] -    # Entire region
        prefix[row2 + 1][col1] -        # Subtract left region
        prefix[row1][col2 + 1] +        # Subtract top region
        prefix[row1][col1]              # Add back double-subtracted region
    )

# Difference Array
def build_difference_array(arr):
    """Build difference array for modifications."""
    n = len(arr)
    diff = [0] * (n + 1)
    diff[0] = arr[0]
    
    for i in range(1, n):
        diff[i] = arr[i] - arr[i-1]
    
    return diff

def range_update(diff, left, right, value):
    """Add value to all elements in range [left, right]."""
    diff[left] += value
    if right + 1 < len(diff):
        diff[right + 1] -= value

def reconstruct_array(diff):
    """Reconstruct original array from difference array."""
    arr = [0] * (len(diff) - 1)
    arr[0] = diff[0]
    
    for i in range(1, len(arr)):
        arr[i] = arr[i-1] + diff[i]
    
    return arr

# Example: Find Continuous Subarray with Target Sum
def find_subarray_with_sum(arr, target):
    """Find continuous subarray that sums to target."""
    prefix_sum = 0
    sum_map = {0: -1}  # Map prefix sum to index
    
    for i, num in enumerate(arr):
        prefix_sum += num
        
        if prefix_sum - target in sum_map:
            return [sum_map[prefix_sum - target] + 1, i]
        
        sum_map[prefix_sum] = i
    
    return []  # No subarray found

# Example: Matrix Block Sum
def matrix_block_sum(mat, K):
    """
    Calculate sum of all elements in block centered at each position.
    Block size is (2K+1) x (2K+1)
    """
    rows, cols = len(mat), len(mat[0])
    # Build prefix sum matrix
    prefix = build_2d_prefix_sum(mat)
    
    # Calculate block sums
    result = [[0] * cols for _ in range(rows)]
    for i in range(rows):
        for j in range(cols):
            # Calculate block boundaries
            r1 = max(0, i - K)
            c1 = max(0, j - K)
            r2 = min(rows - 1, i + K)
            c2 = min(cols - 1, j + K)
            
            # Get sum for this block
            result[i][j] = get_region_sum(prefix, r1, c1, r2, c2)
    
    return result
```

#### Common Applications:

1. **Range Sum Queries**
   - Subarray sums
   - Running averages
   - Cumulative statistics
   - Range updates (with difference array)

2. **2D Region Queries**
   - Matrix block sum
   - Image integral
   - Region averages
   - Heat maps

3. **Difference Array Applications**
   - Range updates
   - Booking problems
   - Temperature changes
   - Height map modifications

4. **Equilibrium Problems**
   - Find pivot index
   - Balance point
   - Equal partition
   - Center of mass

#### Time/Space Complexity:
- Preprocessing Time: O(n) for 1D, O(m×n) for 2D
- Query Time: O(1) for both 1D and 2D
- Space: O(n) for 1D, O(m×n) for 2D
- Difference Array: O(1) per update, O(n) for reconstruction

#### Common Variations:
1. **Prefix Product**
   - Similar to prefix sum but uses multiplication
   - Useful for range product queries
   - Handle zero values carefully

2. **Prefix XOR**
   - Uses XOR operation instead of addition
   - Useful for finding XOR of ranges
   - Common in bit manipulation problems

3. **Prefix Max/Min**
   - Keeps track of running maximum/minimum
   - Useful for sliding window problems
   - Can be combined with monotonic stack

4. **Multiple Prefix Sums**
   - Maintain multiple prefix arrays
   - Used for complex conditions
   - Combine with hash maps for optimization

#### Tips and Tricks:
1. Use 1-based indexing for simpler range queries
2. Handle empty ranges correctly
3. Consider using long integers for large sums
4. Watch for integer overflow in products
5. Optimize space for specific problem constraints
6. Consider sparse array optimizations
7. Use difference array for multiple updates

### 14. Topological Sort Pattern

Topological Sort is an algorithm for ordering vertices in a directed acyclic graph (DAG) such that for each directed edge u→v, vertex u comes before v in the ordering. This pattern is crucial for solving problems involving dependencies or sequential ordering.

#### When to use:
- Course scheduling problems
- Build system dependencies
- Task scheduling with prerequisites
- Project management dependencies
- Package/library dependencies
- Assembly instructions
- Process scheduling in operating systems
- Data processing pipelines

#### Key Concepts:
1. Directed Acyclic Graph (DAG)
   - No cycles allowed
   - Directed edges represent dependencies
   - Must have at least one vertex with no incoming edges

2. Indegree
   - Number of incoming edges to a vertex
   - Vertices with indegree 0 can start first

3. Cycle Detection
   - Important to verify if graph is actually a DAG
   - Presence of cycle means no valid ordering exists

4. Multiple Valid Orders
   - There can be multiple valid topological orderings
   - Any valid ordering satisfies all dependencies

#### Template Code:
```python
from collections import defaultdict, deque

# Kahn's Algorithm (BFS approach)
def topological_sort_bfs(n, prerequisites):
    """
    n: number of vertices
    prerequisites: list of [course, prerequisite] pairs
    Returns topological order if possible, empty list if cycle exists
    """
    # Build adjacency list and calculate indegree
    graph = defaultdict(list)
    indegree = [0] * n
    
    for course, prereq in prerequisites:
        graph[prereq].append(course)
        indegree[course] += 1
    
    # Initialize queue with all 0 indegree vertices
    queue = deque([i for i in range(n) if indegree[i] == 0])
    result = []
    
    while queue:
        # Process current vertex
        vertex = queue.popleft()
        result.append(vertex)
        
        # Reduce indegree for all neighbors
        for neighbor in graph[vertex]:
            indegree[neighbor] -= 1
            # If neighbor has no more dependencies, add to queue
            if indegree[neighbor] == 0:
                queue.append(neighbor)
    
    # Check if all vertices are included (no cycle)
    return result if len(result) == n else []

# DFS approach with cycle detection
def topological_sort_dfs(n, prerequisites):
    """
    DFS-based topological sort with cycle detection
    Returns empty list if cycle exists
    """
    # Build adjacency list
    graph = defaultdict(list)
    for course, prereq in prerequisites:
        graph[prereq].append(course)
    
    # Track vertex states
    # 0: unvisited, 1: visiting (in current path), 2: visited
    visited = [0] * n
    result = []
    
    def dfs(vertex):
        # Check for cycle
        if visited[vertex] == 1:
            return False  # Cycle detected
        if visited[vertex] == 2:
            return True   # Already processed
        
        # Mark as visiting
        visited[vertex] = 1
        
        # Visit all neighbors
        for neighbor in graph[vertex]:
            if not dfs(neighbor):
                return False
        
        # Mark as visited and add to result
        visited[vertex] = 2
        result.append(vertex)
        return True
    
    # Try to visit all vertices
    for vertex in range(n):
        if visited[vertex] == 0:
            if not dfs(vertex):
                return []  # Cycle detected
    
    # Return reversed result (DFS builds in reverse order)
    return result[::-1]

# Example: Course Schedule
def can_finish_courses(num_courses, prerequisites):
    """
    Determine if it's possible to finish all courses
    Returns True if possible, False if cycle exists
    """
    # Build graph
    graph = defaultdict(list)
    indegree = [0] * num_courses
    
    for course, prereq in prerequisites:
        graph[prereq].append(course)
        indegree[course] += 1
    
    # Find courses with no prerequisites
    queue = deque([i for i in range(num_courses) if indegree[i] == 0])
    completed = 0
    
    while queue:
        current = queue.popleft()
        completed += 1
        
        for next_course in graph[current]:
            indegree[next_course] -= 1
            if indegree[next_course] == 0:
                queue.append(next_course)
    
    return completed == num_courses

# Example: Alien Dictionary
def alien_dictionary(words):
    """
    Given a sorted dictionary of an alien language,
    find the order of characters in the alphabet
    """
    # Build graph of character relationships
    graph = defaultdict(set)
    indegree = defaultdict(int)
    chars = set(''.join(words))
    
    # Compare adjacent words to build graph
    for i in range(len(words) - 1):
        w1, w2 = words[i], words[i + 1]
        min_len = min(len(w1), len(w2))
        
        # Find first differing character
        for j in range(min_len):
            if w1[j] != w2[j]:
                if w2[j] not in graph[w1[j]]:
                    graph[w1[j]].add(w2[j])
                    indegree[w2[j]] += 1
                break
        else:
            # Check if longer word comes after shorter word
            if len(w1) > len(w2):
                return ""  # Invalid ordering
    
    # Perform topological sort
    queue = deque([c for c in chars if indegree[c] == 0])
    result = []
    
    while queue:
        char = queue.popleft()
        result.append(char)
        
        for next_char in graph[char]:
            indegree[next_char] -= 1
            if indegree[next_char] == 0:
                queue.append(next_char)
    
    # Check if valid ordering exists
    return ''.join(result) if len(result) == len(chars) else ""
```

#### Common Applications:

1. **Academic Planning**
   - Course prerequisites
   - Degree requirements
   - Learning paths
   - Curriculum design

2. **Build Systems**
   - Dependency resolution
   - Compilation order
   - Deployment sequences
   - Resource allocation

3. **Task Scheduling**
   - Project management
   - Job scheduling
   - Pipeline processing
   - Workflow automation

4. **Software Dependencies**
   - Package management
   - Module loading
   - Service startup
   - Configuration loading

#### Time/Space Complexity:
- Time: O(V + E) for both BFS and DFS approaches
- Space: O(V + E) for graph representation
- Additional Space: O(V) for queue/stack and visited array

#### Common Variations:

1. **Priority-based Topological Sort**
   - Include weights or priorities
   - Optimize for specific metrics
   - Handle resource constraints

2. **Partial Ordering**
   - Not all relationships defined
   - Multiple valid solutions
   - Optimize for specific criteria

3. **Dynamic Updates**
   - Adding new dependencies
   - Removing dependencies
   - Updating existing relationships

4. **Parallel Execution**
   - Group independent tasks
   - Minimize execution time
   - Resource allocation

#### Tips and Tricks:
1. Always check for cycles before processing
2. Consider both BFS and DFS approaches
3. Handle empty graphs and single vertices
4. Verify all vertices are reachable
5. Consider using adjacency matrix for dense graphs
6. Cache results for repeated queries
7. Handle invalid input gracefully

#### Common Pitfalls:
1. Forgetting to check for cycles
2. Not handling disconnected components
3. Assuming unique solution exists
4. Overlooking empty or invalid input
5. Not considering self-loops
6. Ignoring vertex isolation
7. Missing edge cases in prerequisites

### 15. Reservoir Sampling Pattern

Reservoir sampling is a family of randomized algorithms for selecting k samples from a population of n items, where n is either very large or unknown. This pattern is particularly useful when dealing with streams of data or when you need to maintain a representative sample of a large dataset.

#### When to use:
- Selecting random elements from a data stream
- Sampling from very large datasets
- Random sampling without replacement
- Load balancing across servers
- A/B testing with unknown population size
- Random subset selection from linked lists
- Distributed random sampling

#### Key Concepts:
1. Uniform Probability
   - Each element should have equal probability of being selected
   - Probability should be k/n for each element

2. Constant Space
   - Only need to store k elements
   - Independent of stream size

3. Single Pass
   - Process each element exactly once
   - Cannot store all elements in memory

4. Random Selection
   - Use random number generator
   - Maintain selection probability

#### Template Code:
```python
import random

# Single item reservoir sampling
def reservoir_sample_one(stream):
    """
    Select one random element from a stream with uniform probability.
    """
    result = None
    count = 0
    
    for item in stream:
        count += 1
        # Probability of selecting this item is 1/count
        if random.random() < 1.0/count:
            result = item
    
    return result

# K-item reservoir sampling
def reservoir_sample_k(stream, k):
    """
    Select k random elements from a stream with uniform probability.
    """
    reservoir = []
    count = 0
    
    for item in stream:
        count += 1
        
        if len(reservoir) < k:
            # Fill reservoir until we have k items
            reservoir.append(item)
        else:
            # Randomly decide whether to replace an existing item
            # Probability of selecting this item is k/count
            j = random.randrange(count)
            if j < k:
                reservoir[j] = item
    
    return reservoir

# Weighted reservoir sampling
def weighted_reservoir_sample(stream_with_weights):
    """
    Select one item from stream where each item has a weight.
    Probability of selection is proportional to weight.
    """
    result = None
    total_weight = 0
    current_weight = 0
    
    for item, weight in stream_with_weights:
        total_weight += weight
        # Select this item with probability weight/total_weight
        if random.random() < weight/total_weight:
            result = item
    
    return result

# Example: Random node from linked list
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class LinkedListRandomNode:
    def __init__(self, head):
        self.head = head
    
    def get_random(self):
        """
        Returns a random node's value from the linked list.
        Each node must have equal probability of being chosen.
        """
        result = None
        current = self.head
        count = 0
        
        while current:
            count += 1
            # Probability of selecting this node is 1/count
            if random.random() < 1.0/count:
                result = current.val
            current = current.next
        
        return result

# Example: Random subset of array
class RandomizedSet:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.nums = []
        self.pos = {}  # val -> position mapping
    
    def insert(self, val: int) -> bool:
        """
        Inserts an item val into the set if not present.
        Returns true if the item was not present, false otherwise.
        """
        if val in self.pos:
            return False
        
        self.nums.append(val)
        self.pos[val] = len(self.nums) - 1
        return True
    
    def remove(self, val: int) -> bool:
        """
        Removes an item val from the set if present.
        Returns true if the item was present, false otherwise.
        """
        if val not in self.pos:
            return False
        
        # Move the last element to the position of element to delete
        last_val = self.nums[-1]
        idx = self.pos[val]
        
        self.nums[idx] = last_val
        self.pos[last_val] = idx
        
        # Remove the last element
        self.nums.pop()
        del self.pos[val]
        return True
    
    def getRandom(self) -> int:
        """
        Get a random element from the set.
        Each element must have the same probability of being returned.
        """
        return random.choice(self.nums)
```

#### Common Applications:

1. **Data Streaming**
   - Online sampling
   - Stream processing
   - Real-time analytics
   - Log sampling

2. **Load Balancing**
   - Server selection
   - Task distribution
   - Resource allocation
   - Request routing

3. **Testing and Debugging**
   - Test case selection
   - Error sampling
   - Performance monitoring
   - Debug log sampling

4. **Machine Learning**
   - Dataset sampling
   - Cross-validation
   - Mini-batch selection
   - Random forest building

#### Time/Space Complexity:
- Time per element: O(1)
- Space: O(k) where k is sample size
- Total time: O(n) for n elements
- Auxiliary space: O(1) for random number generation

#### Common Variations:

1. **Weighted Sampling**
   - Elements have different probabilities
   - Weight-based selection
   - Priority sampling
   - Importance sampling

2. **Distributed Sampling**
   - Parallel processing
   - Distributed streams
   - Shared state
   - Consensus protocols

3. **Adaptive Sampling**
   - Dynamic sample size
   - Conditional sampling
   - Stratified sampling
   - Systematic sampling

4. **Time-Based Sampling**
   - Time-window sampling
   - Decay-based sampling
   - Periodic sampling
   - Event-triggered sampling

#### Tips and Tricks:
1. Use good random number generator
2. Handle edge cases (empty stream, k=0)
3. Consider thread safety for concurrent access
4. Maintain sample statistics if needed
5. Consider using numpy for large-scale operations
6. Cache results when appropriate
7. Monitor memory usage for large k

#### Common Pitfalls:
1. Not maintaining uniform probability
2. Incorrect handling of duplicates
3. Memory leaks in long-running streams
4. Poor random number generation
5. Race conditions in concurrent scenarios
6. Overflow in count variables
7. Biased sampling due to rounding

#### Best Practices:
1. Document probability distribution
2. Validate input parameters
3. Use appropriate data structures
4. Handle stream interruptions
5. Implement proper error handling
6. Consider performance implications
7. Test with different stream sizes
