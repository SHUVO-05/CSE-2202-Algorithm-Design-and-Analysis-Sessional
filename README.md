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
- 

# Lab 03

## Experiment 05: Implementation and Complexity Comparison of Recursive and Iterative Quick Sort Algorithms

### Objective
- To understand the Divide and Conquer paradigm.
- To implement Quick Sort using both recursive and iterative approaches.
- To compare the performance and complexity of both implementations on different input sizes.
- To analyze the space and time efficiency for real-world large data inputs.

### Algorithm
Quick Sort Algorithm uses the Divide and Conquer strategy:

- **Divide:** Choose a pivot and partition the array into two subarrays such that elements less than pivot go to the left, and greater than pivot go to the right.
- **Conquer:** Recursively or iteratively apply the same strategy to left and right subarrays.
- **Combine:** No combining is needed, as sorting happens during the recursive return.

### Theoretical Solution of the Problem

| Case          | Time Complexity          |
|---------------|--------------------------|
| Best Case     | O(n log n)               |
| Average Case  | O(n log n)               |
| Worst Case   | O(n²) (when pivot is worst) |

- **Space Complexity (Recursive):** O(log n) auxiliary space due to recursion stack.
- **Space Complexity (Iterative):** O(n) auxiliary stack (manually implemented).
## Practical Work

### a. Pseudocode

#### Recursive Quick Sort

```plaintext
QUICKSORT(arr, low, high)
  if low < high
    pivotIndex ← PARTITION(arr, low, high)
    QUICKSORT(arr, low, pivotIndex - 1)
    QUICKSORT(arr, pivotIndex + 1, high)
```

### Iterative Quick Sort Pseudocode

```plaintext
ITERATIVE_QUICKSORT(arr, low, high)
  Create stack
  push(low, high) to stack

  while stack is not empty
    (low, high) ← pop()
    pivotIndex ← PARTITION(arr, low, high)
    
    if pivotIndex - 1 > low
      push(low, pivotIndex - 1)
    if pivotIndex + 1 < high
      push(pivotIndex + 1, high)
```
### b. Source Code in C++

```cpp
#include <iostream>
#include <stack>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

// Recursive Quick Sort
void quickSortRecursive(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSortRecursive(arr, low, pi - 1);
        quickSortRecursive(arr, pi + 1, high);
    }
}

// Iterative Quick Sort
void quickSortIterative(int arr[], int low, int high) {
    stack<pair<int, int>> s;
    s.push({low, high});
    while (!s.empty()) {
        low = s.top().first;
        high = s.top().second;
        s.pop();

        int pi = partition(arr, low, high);
        if (pi - 1 > low)
            s.push({low, pi - 1});
        if (pi + 1 < high)
            s.push({pi + 1, high});
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}
```
## Analysis Table

| Algorithm           | Best Case   | Worst Case | Avg Case   | Space   |
|---------------------|-------------|------------|------------|---------|
| Quick Sort Recursive | O(n log n)  | O(n²)      | O(n log n) | O(log n)|
| Quick Sort Iterative | O(n log n)  | O(n²)      | O(n log n) | O(n)    |

---

## Observations

- Recursive approach is simpler and easier to implement.
- Iterative quick sort avoids function call overhead but requires manual stack handling.
- For large arrays, both versions are significantly faster than Bubble or Insertion Sort.
- Recursive version may hit stack overflow for very large datasets without tail call optimization.

---

## Challenges

- Stack management in the iterative approach was tricky.
- Ensuring correct pivot and partition logic during both versions.
- Measuring and comparing execution times manually required precision.

---

## Conclusion

Quick Sort is an efficient sorting algorithm that benefits from the divide and conquer technique. While both recursive and iterative implementations perform similarly in time complexity, the recursive version is more readable. However, for applications where stack depth is a concern, the iterative version offers better control over memory usage.

---

# Lab 04  
## Greedy Algorithms – Coin Change Problem

### Experiment 06: Greedy Algorithms – Coin Change Problem

#### Objective
- Understand the concept of the Greedy Algorithm.
- Implement the Coin Change problem using the greedy approach.
- Compare the greedy solution with the optimal solution.
- Analyze the time and space complexity of the algorithm.

#### Algorithm

Greedy Coin Change Algorithm:  
At each step, select the largest coin denomination that is less than or equal to the remaining amount. Subtract that coin's value from the remaining amount and repeat until the amount reaches zero.

#### Theoretical Solution of the Given Problem

- **Input:** a set of coin denominations and a target amount.  
- **Output:** minimum number of coins required to make the target amount.  
- Greedy approach is fast but may **not always give the optimal solution**.  
- For denominations like `[1, 5, 10, 25]`, greedy **always gives the optimal solution**.  
- For denominations like `[1, 3, 4]`, greedy **may fail** to give the optimal solution.

---

## Practical Work
### b. Source Code (C++)

```cpp
#include <iostream>
using namespace std;

int greedyCoinChange(int coins[], int n, int amount) {
    int count = 0;
    for (int i = 0; i < n; i++) {
        while (amount >= coins[i]) {
            amount -= coins[i];
            count++;
        }
    }
    return count;
}

int main() {
    int coins[] = {25, 10, 5, 1};  // descending order
    int n = sizeof(coins) / sizeof(coins[0]);
    int amount;

    cout << "Enter amount: ";
    cin >> amount;

    int result = greedyCoinChange(coins, n, amount);
    cout << "Minimum coins required (Greedy): " << result << endl;

    return 0;
}
```
## Analysis Table

| Amount | Coins Used (Greedy)           | Minimum Coins (Optimal) | Greedy Correct? |
|--------|------------------------------|------------------------|-----------------|
| 30     | 2 (25 + 5)                   | 2                      | Yes             |
| 6      | 3 (4 + 1 + 1)                | 2 (3 + 3)              | No              |
| 49     | 7 (25 + 10 + 10 + 1 + 1 + 1 + 1) | 7                      | Yes             |

---

| Algorithm           | Best Case | Worst Case | Average Case | Space Complexity |
|---------------------|-----------|------------|--------------|------------------|
| Greedy Coin Change   | O(n)      | O(n)       | O(n)         | O(1)             |

---

### Observations
- Greedy algorithm is simple and fast.
- Greedy does not always provide the optimal solution for all coin sets.
- It works optimally with classic coin denominations like US coins.
- For some unusual coin sets, greedy fails and other algorithms (like dynamic programming) are needed.

### Challenges
- If the coin denominations are unordered, sorting is required first.
- Some coin sets cannot be solved optimally with greedy; other methods are necessary.

### Conclusion
This lab helped understand the Greedy Algorithm paradigm and its application to the Coin Change problem. Greedy uses less time and memory but does not always guarantee optimality. Therefore, the choice of algorithm depends on the problem type.

---

# Lab 05  
## Greedy Algorithm – Fractional Knapsack Problem

### Experiment 07: Greedy Algorithm – Fractional Knapsack Problem

### Objective
- To understand and apply the greedy strategy to the Knapsack Problem.
- To implement the Fractional Knapsack algorithm.
- To compare Greedy (Fractional) Knapsack with the optimal 0/1 Knapsack.
- To analyze the time and space complexity.

### Algorithm
Greedy Strategy:
- Compute value per unit weight for each item.
- Sort all items in decreasing order of value/weight.
- Traverse sorted items:
  - Take the full item if it fits.
  - Take the possible fraction if the full item doesn't fit.

### Theoretical Solution
- Given:
  - n items with weights `w[i]` and values `v[i]`
  - Knapsack capacity `W`
- Goal:
  - Maximize total value in knapsack allowing fraction of items.
- Approach:
  - Greedy selection based on value/weight ratio.
- Time Complexity:
  - Sorting: O(n log n)
  - Selection: O(n)
  - → Total: O(n log n)
- Space Complexity:
  - Storing items and ratios → O(n)

---

### Practical Work
## b. Source Code (C++)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

struct Item {
    float weight, value;
};

bool compare(Item a, Item b) {
    return (a.value / a.weight) > (b.value / b.weight);
}

float fractionalKnapsack(vector<Item>& items, float capacity) {
    sort(items.begin(), items.end(), compare);
    
    float totalValue = 0.0;

    for (auto& item : items) {
        if (capacity >= item.weight) {
            totalValue += item.value;
            capacity -= item.weight;
        } else {
            totalValue += item.value * (capacity / item.weight);
            break;
        }
    }

    return totalValue;
}

int main() {
    int n;
    float capacity;
    cout << "Enter number of items: ";
    cin >> n;
    cout << "Enter knapsack capacity: ";
    cin >> capacity;

    vector<Item> items(n);
    for (int i = 0; i < n; i++) {
        cout << "Enter value and weight of item " << i + 1 << ": ";
        cin >> items[i].value >> items[i].weight;
    }

    float maxValue = fractionalKnapsack(items, capacity);
    cout << "Maximum value in Knapsack = " << maxValue << endl;
    return 0;
}
```

# Analysis Table

| Algorithm          | Best Case   | Worst Case  | Avg Case    | Space    |
|--------------------|-------------|-------------|-------------|----------|
| Fractional Knapsack | O(n log n)  | O(n log n)  | O(n log n)  | O(n)     |

---

# Comparison Table (Empirical)

| Items (Value, Weight)                  | Capacity | Greedy Value | Optimal Value (0/1) | Greedy Correct? |
|--------------------------------------|----------|--------------|---------------------|-----------------|
| (60, 10), (100, 20), (120, 30)       | 50       | 240          | 240                 | ✅              |
| (30, 10), (20, 20), (100, 30)        | 50       | 160          | 160                 | ✅              |
| (60, 10), (100, 20), (120, 30)       | 40       | 200          | 220 (0/1)           | ❌              |

---

# Observations

- Greedy algorithm performs well when fractional items are allowed.
- Greedy fails to produce optimal results when only whole items are allowed (0/1 Knapsack).
- Sorting by value-to-weight ratio is crucial for accuracy.
- For large input sizes, Greedy gives fast and close-to-optimal solutions.

---

# Challenges

- Understanding where greedy fails compared to dynamic programming.
- Implementing proper sorting based on value/weight ratio.
- Handling floating-point fractions precisely.

---

# Conclusion

- Greedy strategy is effective for Fractional Knapsack, providing near-optimal results efficiently.
- However, it cannot be used for 0/1 Knapsack, where dynamic programming is more suitable.
- It is important to choose the right algorithm depending on the nature of the problem.

---

# Lab 06  
**Experiment 08:** Implementation of Fibonacci Series using Recursion and Dynamic Programming

---

## Objective

- To implement Fibonacci Series using recursion, memoization, and tabulation.
- To understand and apply Dynamic Programming principles.
- To compare time and space complexity across different implementations.
- To visualize overlapping sub-problems and optimal substructure.

---

## Algorithm

### Fibonacci Recursive Algorithm

