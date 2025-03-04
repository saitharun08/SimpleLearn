# Time Complexity (Big-O, Big-Theta, Big-Omega)

Time complexity is the computation of the amount of time an algorithm takes to complete based on the input size. It's crucial for understanding how efficient an algorithm is.

---

## Big-O Notation (O)

- **Definition**: Represents the upper bound of the time complexity.
- **Usage**: Describes the worst-case scenario (maximum time).
- **Example**: 
  - If an algorithm takes `O(n)` time, its execution time increases linearly with input size.
  - A loop that runs `n` times is `O(n)`.
  - A loop nested inside another loop that runs `n` times each is `O(n²)`.

---

## Big-Theta Notation (Θ)

- **Definition**: Represents the tight bound of the time complexity.
- **Usage**: Describes the exact behavior of an algorithm in both the worst-case and best-case.
- **Implication**: The algorithm's time complexity is bounded from above and below by the same function.
- **Example**: 
  - If an algorithm is `Θ(n)`, it means that the execution time increases linearly in both best and worst cases.

---

## Big-Omega Notation (Ω)

- **Definition**: Represents the lower bound of the time complexity.
- **Usage**: Describes the best-case scenario (minimum time).
- **Implication**: The algorithm takes at least a certain amount of time.
- **Example**: 
  - If an algorithm is `Ω(n)`, it means that the execution time will always be at least proportional to `n`.

---

# How to Analyze Time Complexity

### Constant Time - `O(1)`

- **Description**: Time doesn't depend on the input size.
- **Example**: Accessing an element in an array by its index.

### Logarithmic Time - `O(log n)`

- **Description**: Time grows logarithmically with the input size.
- **Example**: Binary search in a sorted array.

### Linear Time - `O(n)`

- **Description**: Time grows linearly with the input size.
- **Example**: Traversing through a list or array.

### Quadratic Time - `O(n²)`

- **Description**: Time grows quadratically with the input size.
- **Example**: Nested loops iterating over the input.

### Cubic Time - `O(n³)`

- **Description**: Time grows cubically with the input size.
- **Example**: Triple nested loops.

### Exponential Time - `O(2^n)`

- **Description**: Time grows exponentially with the input size.
- **Example**: Algorithms that solve the traveling salesman problem.

---

# Key Concepts to Understand

- **Worst-case vs. Best-case vs. Average-case**: Time complexity is often analyzed under the worst-case scenario, but it can also be analyzed for best and average cases.
- **Amortized Time Complexity**: Used for algorithms where the time complexity varies but averages out to a constant time over a sequence of operations.

---

# Practice Problems

### Example 1

Consider the following algorithm:

```python
def example(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            print(arr[i], arr[j])
```

What is the time complexity? 

### Example 2

Consider the following algorithm:

```python
def example(arr):
    for i in range(len(arr)):
        print(arr[i])

```

What is the time complexity? 

---

# Detailed Explanation with Examples:

---

### Example 1: O(n)
```python
def print_elements(arr):
    for i in range(len(arr)):
        print(arr[i])
```

- **Time Complexity**: O(n)
- **Reason**: The loop runs `n` times, where `n` is the length of the array. Each iteration takes constant time, so the time complexity is directly proportional to the size of the input (`n`).

---

### Example 2: O(n²)
```python
def print_pairs(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            print(arr[i], arr[j])
```

- **Time Complexity**: O(n²)
- **Reason**: Here, we have two nested loops, each of which runs `n` times. As a result, the total number of iterations is `n * n = n²`, leading to a time complexity of `O(n²)`.

---

### Example 3: O(log n) (Binary Search)

In binary search, the input array is divided in half at each step. So, the algorithm essentially reduces the problem size by half with each comparison.

```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

- **Time Complexity**: O(log n)
- **Reason**: In binary search, the input array is split into half each time (hence logarithmic). If the array size is 16, it will take at most 4 comparisons (`log₂ 16 = 4`). This is the essence of `O(log n)`.

---

### Example 4: O(n log n) (Merge Sort)

Merge Sort works by recursively dividing the array in half (`log n`) and then merging the halves in linear time (`n`).

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1
```

- **Time Complexity**: O(n log n)
- **Reason**: The array is recursively divided in half, which gives us `log n` levels. On each level, we do a linear scan of the array, resulting in `O(n)` work at each level. Thus, we get `O(n log n)` time complexity.

---

### Example 5: O(2^n) (Recursive Fibonacci)

The Fibonacci sequence can be computed using a recursive approach, but this comes with exponential time complexity.

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```

- **Time Complexity**: O(2^n)
- **Reason**: In each call to the Fibonacci function, two more recursive calls are made, which results in an exponential growth of function calls.

---

## Practice Problems:

### Problem 1:
```python
def find_max(arr):
    max_val = arr[0]
    for num in arr:
        if num > max_val:
            max_val = num
    return max_val
```

- **Question**: What is the time complexity of this function?


---

### Problem 2:
```python
def two_sum(arr, target):
    for i in range(len(arr)):
        for j in range(i+1, len(arr)):
            if arr[i] + arr[j] == target:
                return (i, j)
```

- **Question**: What is the time complexity of this function?
---

### Problem 3:
```python
def contains_duplicates(arr):
    seen = set()
    for num in arr:
        if num in seen:
            return True
        seen.add(num)
```

- **Question**: What is the time complexity of this function?

---

## Analyzing Worst, Best, and Average Case Scenarios:

- **Worst-case**: This is the maximum time complexity the algorithm will take for a given input size.
  - Example: In binary search, the worst-case time complexity is `O(log n)` because you may need to search through all levels of the tree.

- **Best-case**: This is the minimum time complexity for an algorithm, assuming the best possible input.
  - Example: For linear search, the best-case is `O(1)` if the element is at the first position in the array.

- **Average-case**: This is the expected time complexity under normal circumstances.
  - Example: For quicksort, the average-case time complexity is `O(n log n)`.

---

## Key Points to Remember:

- **Big-O** tells you the worst-case performance.
- **Big-Theta** tells you the exact performance.
- **Big-Omega** tells you the best-case performance.
- Always focus on the highest-order term (e.g., `O(n²)` is greater than `O(n)`).
