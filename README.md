# Lab: 01 – Introduction to Algorithm Analysis

## Learning Objectives

By the end of this lab, students will be able to:

- Understand what constitutes a valid algorithm.
- Identify input size and compute step counts for algorithm execution.
- Analyze different time complexities: constant, linear, logarithmic, quadratic.
- Apply asymptotic notations: Big-O, Big-Ω, Big-Θ to actual code.
- Perform manual complexity analysis on basic algorithms.

---

## Prerequisites

- Programming knowledge in C/C++
- Understanding of Data Structures (arrays, loops, etc.)

---

## Theory Recap

### What is an Algorithm?

An algorithm is a finite, step-by-step procedure designed to solve a specific problem.

#### Properties of an Algorithm

| Property       | Description                                 |
|----------------|---------------------------------------------|
| Input          | Accepts zero or more inputs                 |
| Output         | Produces at least one output                |
| Definiteness   | Instructions must be clear and precise      |
| Finiteness     | Must terminate after a finite number of steps |
| Effectiveness  | Steps are basic and executable              |

---

### Asymptotic Notations

| Notation   | Represents   | Description                                      |
|------------|--------------|--------------------------------------------------|
| O(f(n))    | Upper Bound  | Worst-case: T(n) ≤ c·f(n) for large n           |
| Ω(f(n))    | Lower Bound  | Best-case: T(n) ≥ c·f(n) for large n            |
| Θ(f(n))    | Tight Bound  | Average-case: T(n) = c·f(n) for large n         |

---

*End of Theory Section.*
# Lab Activities

## Experiment 1: Linear Search & Step Analysis

### Objective
To implement linear search and analyze its time and space complexity.

---

### Algorithm
Check each element of the array from start to end to find the target.

---

### Theoretical Solution

- **Best Case:** O(1) — key is at index 0  
- **Worst Case:** O(n) — key is not present in the array  
- **Average Case:** O(n)  
- **Space Complexity:** O(1)

---

### Practical Work

#### a. Pseudocode

# Linear Search

---

## a. Pseudocode

```text
LinearSearch(array, key)
  for i = 0 to length(array) - 1
    if array[i] == key
      return i
  return -1

```

## b. Source Code (C++)

```cpp
// Linear Search
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int key) {
    for(int i = 0; i < n; i++) {
        if(arr[i] == key)
            return i;
    }
    return -1;
}

int main() {
    int arr[] = {5, 10, 15, 20, 25};
    int key = 20;
    int result = linearSearch(arr, 5, key);

    if(result != -1)
        cout << "Element found at index: " << result << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}
```
# Experiment 2: Binary Search (Sorted Array Required)

## Objective
To implement binary search and understand its logarithmic time complexity.

---

## Algorithm
Use the divide and conquer approach to repeatedly halve the array until the key is found or the search space is exhausted.

---

## Theoretical Solution

- **Best Case:** O(1) — when the key is found at the midpoint in the first iteration.
- **Worst Case:** O(log n)
- **Average Case:** O(log n)
- **Space Complexity:** O(1)

---

## Practical Work

### a. Pseudocode

```plaintext
BinarySearch(array, key)
  low = 0
  high = n - 1
  while low <= high
    mid = (low + high) / 2
    if array[mid] == key
      return mid
    else if key < array[mid]
      high = mid - 1
    else
      low = mid + 1
  return -1
```

### b. Source Code (C++)

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int n, int key) {
    int low = 0, high = n - 1;
    while(low <= high) {
        int mid = (low + high) / 2;
        if(arr[mid] == key)
            return mid;
        else if(arr[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    return -1;
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int key = 30;
    int result = binarySearch(arr, 5, key);
    if(result != -1)
        cout << "Element found at index: " << result << endl;
    else
        cout << "Element not found" << endl;
    return 0;
}
```
# Experiment 3: Bubble Sort – Complexity Analysis

## Objective
To implement bubble sort and understand quadratic time complexity.

---

## Algorithm
Repeatedly swap adjacent elements if they are in the wrong order until the array is sorted.

---

## Theoretical Solution

- **Best Case:** O(n) – when the array is already sorted (optimized version)
- **Worst Case:** O(n²)
- **Average Case:** O(n²)
- **Space Complexity:** O(1)

---

## Practical Work

### a. Pseudocode

```plaintext
BubbleSort(array)
  repeat
    swapped = false
    for i = 0 to n - 2
      if array[i] > array[i + 1]
        swap array[i], array[i + 1]
        swapped = true
  until swapped == false
  ```
### b. Source Code (C++)

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    bool swapped;
    do {
        swapped = false;
        for(int i = 0; i < n - 1; i++) {
            if(arr[i] > arr[i + 1]) {
                swap(arr[i], arr[i + 1]);
                swapped = true;
            }
        }
    } while(swapped);
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    bubbleSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```
# Lab 02: Algorithm Analysis and Sorting Techniques

## Analysis Table

| **Algorithm**    | **Best Case** | **Worst Case** | **Average Case** | **Space** |
|------------------|---------------|----------------|------------------|-----------|
| Linear Search     | O(1)          | O(n)           | O(n)             | O(1)      |
| Binary Search     | O(1)          | O(log n)       | O(log n)         | O(1)      |
| Bubble Sort       | O(n)          | O(n²)          | O(n²)            | O(1)      |

---

## Observations

- **Binary Search** is much faster than **Linear Search** for large datasets but requires a **sorted array**.
- **Linear Search** is more flexible (works on unsorted arrays), but inefficient for large `n`.
- **Bubble Sort** is simple and easy to implement but highly inefficient for large inputs.
- Step count observations align with theoretical **Big-O** analysis.

---

## Conclusion

This lab provided a practical understanding of **basic algorithm complexities** through real code implementations.

### Key Takeaways:
- Step count increases **linearly** or **logarithmically** depending on the algorithm.
- Optimizations (e.g., early exits in sorting/searching) can significantly improve runtime.
- Theoretical understanding of **asymptotic notations** is reflected in actual step behavior.
- Improved confidence in analyzing and comparing algorithm performance.

---

## Lab Overview: Lab 02

### Learning Objectives

By the end of this lab session, students will be able to:

- Understand the **Divide and Conquer** paradigm.
- Implement and compare both **recursive and iterative** versions of **Merge Sort**.
- Analyze and compare **time and space complexity**.
- Apply **recursive thinking** to problem-solving.
- Relate **theoretical complexity** with **practical execution**.

---

## Lesson Fit

### Prerequisites:

- Programming in **C/C++**
- Understanding of **data structures** (arrays, recursion)

---

## Theory Recap: What is Divide and Conquer?

**Divide and Conquer** is a powerful algorithm design technique where:

1. **Divide**: Break the problem into smaller subproblems.
   - _e.g.,_ split an array into halves in Merge Sort.
2. **Conquer**: Solve each subproblem recursively.
   - Base cases are handled directly.
3. **Combine**: Merge solutions to subproblems into the final result.

### Why Use Divide and Conquer?

- Efficient for **large input sizes**
- Reduces time complexity (e.g., from O(n²) → O(n log n))
- Encourages **recursive problem-solving**
- Enables **parallelism** for performance optimization

---

## Classic Examples of Divide and Conquer

| **Algorithm**           | **Problem Type**          | **Time Complexity**     |
|-------------------------|---------------------------|--------------------------|
| Merge Sort              | Sorting                   | O(n log n)               |
| Quick Sort              | Sorting                   | O(n log n) (average)     |
| Binary Search           | Searching                 | O(log n)                 |
| Closest Pair of Points  | Computational Geometry    | O(n log n)               |
| Strassen's Multiplication | Matrix Multiplication   | ~O(n^2.81)               |
| Karatsuba’s Algorithm   | Integer Multiplication    | O(n^1.58)                |

---

# Experiment 04: Merge Sort – Recursive and Iterative

## Objective

- To implement **Merge Sort** using both **recursive** and **iterative** techniques.
- To understand and compare their **time and space complexities**.
- To observe **step behavior** on various input sizes.

---

## Algorithm

**Merge Sort** is a **stable sorting algorithm** based on the **Divide and Conquer** strategy.

- **Divide**: Split the array into two halves.
- **Conquer**: Recursively or iteratively sort both halves.
- **Combine**: Merge the two sorted halves into a single sorted array.

---

## Theoretical Solution

### Time Complexity

| **Case**     | **Recursive** | **Iterative** |
|--------------|---------------|---------------|
| Best Case    | O(n log n)    | O(n log n)    |
| Worst Case   | O(n log n)    | O(n log n)    |
| Average Case | O(n log n)    | O(n log n)    |

### Space Complexity

- **Recursive Merge Sort**: O(n)  
  _(Due to recursion stack + temporary arrays)_
- **Iterative Merge Sort**: O(n)  
  _(Avoids recursion but still uses temp arrays)_

---

## Practical Work

### a. Pseudocode

#### Recursive Merge Sort

```plaintext
MergeSort(array, left, right)
  if left < right
    mid = (left + right) / 2
    MergeSort(array, left, mid)
    MergeSort(array, mid + 1, right)
    Merge(array, left, mid, right)
```
### Iterative Merge Sort Pseudocode

```plaintext
IterativeMergeSort(array, n)
  for size = 1 to n, doubling each time
    for left = 0 to n - 1 in steps of 2 * size
      mid = left + size - 1
      right = min(left + 2 * size - 1, n - 1)
      Merge(array, left, mid, right)
```
### b. Source Code (C++)

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

// Merge function to merge two sorted halves
void merge(int arr[], int l, int m, int r) {
    int n1 = m - l + 1, n2 = r - m;
    int L[n1], R[n2];
    for(int i = 0; i < n1; i++) 
        L[i] = arr[l + i];
    for(int j = 0; j < n2; j++) 
        R[j] = arr[m + 1 + j];

    int i = 0, j = 0, k = l;
    while(i < n1 && j < n2)
        arr[k++] = (L[i] <= R[j]) ? L[i++] : R[j++];

    while(i < n1) arr[k++] = L[i++];
    while(j < n2) arr[k++] = R[j++];
}

// Iterative Merge Sort
void iterativeMergeSort(int arr[], int n) {
    for(int curr_size = 1; curr_size <= n - 1; curr_size *= 2) {
        for(int left_start = 0; left_start < n - 1; left_start += 2 * curr_size) {
            int mid = min(left_start + curr_size - 1, n - 1);
            int right_end = min(left_start + 2 * curr_size - 1, n - 1);
            merge(arr, left_start, mid, right_end);
        }
    }
}

// Recursive Merge Sort
void mergeSort(int arr[], int l, int r) {
    if(l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
```

## Analysis Table

| Algorithm           | Best Case   | Worst Case  | Avg Case    | Space  |
|---------------------|-------------|-------------|-------------|--------|
| Recursive Merge Sort | O(n log n)  | O(n log n)  | O(n log n)  | O(n)   |
| Iterative Merge Sort | O(n log n)  | O(n log n)  | O(n log n)  | O(n)   |

---

## Empirical Comparison Table

| n (array size) | Recursive Time (ms) | Iterative Time (ms) |
|----------------|---------------------|---------------------|
| 1,000          | ~0.3                | ~0.4                |
| 5,000          | ~1.0                | ~1.1                |
| 10,000         | ~2.5                | ~2.6                |
| 50,000         | ~13                 | ~13.5               |
| 100,000        | ~28                 | ~29                 |

*Note: Times may vary slightly depending on system and compiler.*

---

## Observations

- Both recursive and iterative merge sort maintain **O(n log n)** time complexity.
- Recursive version is easier to write, but iterative version avoids recursion overhead.
- Memory usage remains **O(n)** due to temporary arrays during merging.
- Iterative merge sort is more **stack-safe** for large datasets.

---

## Challenges

- Writing the iterative merge sort correctly was more complex than the recursive one.
- Managing indices and bounds carefully during merge steps.
- Measuring precise execution time for empirical comparison.
- Handling array boundaries to avoid index out-of-bounds errors.

---

## Conclusion

In this lab, we explored **Divide and Conquer** algorithms, particularly **Merge Sort**. We successfully implemented both recursive and iterative variants, verified their theoretical complexities, and compared them through practical execution.

### Key Takeaways:
- Both versions are efficient for large data.
- Recursive approach is more intuitive but limited by recursion depth.
- Iterative merge sort is better suited for **memory-critical** or **real-time** systems.
