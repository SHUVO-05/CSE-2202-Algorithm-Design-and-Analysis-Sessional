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

