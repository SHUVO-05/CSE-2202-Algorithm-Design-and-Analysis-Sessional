# Lab 01: Introduction to Algorithm Design & Complexity Analysis

## Learning Objectives

- Define what constitutes an algorithm.
- Identify input size and step count.
- Differentiate between constant, linear, logarithmic, and quadratic complexities.
- Apply Big-O, Big-Ω, and Big-Θ to code.
- Perform basic complexity analysis manually.

---

## Lesson Fit

**Prerequisite:** C/C++, Data Structures

---

## Theory Recap

### What is an Algorithm?

An algorithm is a finite sequence of well-defined steps for solving a problem.

### Asymptotic Notations

| Notation   | Meaning      | Definition                                 |
|------------|--------------|--------------------------------------------|
| O(f(n))    | Upper bound  | Worst-case time: T(n) ≤ c·f(n) for large n |
| Ω(f(n))    | Lower bound  | Best-case time: T(n) ≥ c·f(n)              |
| Θ(f(n))    | Tight bound  | Average-case time: T(n) = c·f(n)           |

---

## Lab 1 Activity

### Experiment 1: Linear Search & Step Analysis

**Time Complexity:**

- Best: O(1) (key at first index)  
- Worst: O(n) (key not present)  
- Average: O(n)

**Space Complexity:** O(1)

---

### Source Code (C++)

```cpp
// Linear Search
#include<iostream>
using namespace std;

void print(int ar[], int siz) {
    for(int i = 0; i < siz; i++)
        cout << ar[i] << ' ';
    cout << endl;
}

void linear_search(int ar[], int siz, int item) {
    int i = 0;
    ar[siz] = item;
    while (ar[i] != item) {
        i++;
    }
    if (i == siz)
        cout << item << " is not found " << endl;
    else
        cout << "Element is found at position " << i + 1 << endl;
}

int main() {
    int item;
    int Array[8] = {321, 150, 235, 65, 573, 5, 789, 1278};
    print(Array, 8);
    cout << "Type your item you want to search: ";
    cin >> item;
    linear_search(Array, 8, item);
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2001/Experiment%2001/Linear%20Search.png)



##  Experiment 2: Binary Search (Sorted Array Required)

### Time & Space Complexity

- **Time Complexity:**
  - Best Case: O(1)
  - Worst Case: O(log n)
- **Space Complexity:** O(1)

---

###  Source Code (C++)

```cpp
// Binary Search
#include<iostream>
using namespace std;

void print(int ar[], int siz) {
    for(int i = 0; i < siz; i++)
        cout << ar[i] << ' ';
    cout << endl;
}

// Only use for sorted array
void Binary_search(int ar[], int len, int item) {
    int lb = 0, ub = len - 1;
    int mid = (lb + ub) / 2;

    while (lb <= ub && ar[mid] != item) {
        if (item < ar[mid])
            ub = mid - 1;
        else
            lb = mid + 1;
        mid = (lb + ub) / 2;
    }

    if (ar[mid] == item)
        cout << "Item " << item << " is found at position " << mid + 1 << endl;
    else
        cout << "Item not found" << endl;
}

// Only use for sorted array
int Binary_search_recursive(int ar[], int lb, int ub, int item) {
    if (lb > ub) return -1;
    int mid = (lb + ub) / 2;

    if (item == ar[mid])
        return mid;
    else if (item < ar[mid])
        return Binary_search_recursive(ar, lb, mid - 1, item);
    else
        return Binary_search_recursive(ar, mid + 1, ub, item);
}

int main() {
    int item;
    int Array[8] = { 5, 65, 150, 235, 321, 573, 789, 1278 };
    print(Array, 8);
    cout << "Enter your item you want to search: ";
    cin >> item;
    Binary_search(Array, 8, item);
}
```

---
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2001/Experiment%2002/Binary%20Search.png)


##  Experiment 3: Bubble Sort

###  Time & Space Complexity

- **Time Complexity:**
  - Best Case: O(n) (when already sorted with optimization)
  - Worst Case: O(n²)
  - Average Case: O(n²)
- **Space Complexity:** O(1)

---

###  Source Code (C++)

```cpp
// Bubble Sort
#include<iostream>
using namespace std;

void print(int ar[], int siz) {
    for(int i = 0; i < siz; i++)
        cout << ar[i] << ' ';
    cout << endl;
}

void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

void bubble_sort(int array[], int siz) {
    int i, j, flag;
    for(i = 0; i < siz - 1; i++) {
        flag = 0;
        for(j = 1; j < siz - i; j++) {
            if(array[j - 1] > array[j]) {
                swap(array[j - 1], array[j]);
                flag = 1;
            }
        }
        if(flag == 0) break;
    }
}

int main() {
    int Array[7] = {56, 0, 5, 0, 3, 9, 1};
    print(Array, 7);
    bubble_sort(Array, 7);
    print(Array, 7);
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2001/Experiment%2003/Boubble%20Sort.png)
---

###  Analysis Table

| Algorithm       | Best Case | Worst Case | Average Case | Space Complexity |
|-----------------|------------|-------------|----------------|-------------------|
| Linear Search   | O(1)       | O(n)        | O(n)           | O(1)              |
| Binary Search   | O(1)       | O(log n)    | O(log n)       | O(1)              |
| Bubble Sort     | O(n)       | O(n²)       | O(n²)          | O(1)              |

---

###  Observations

- **Binary Search** is very efficient but requires sorted input.
- **Linear Search** is simple but inefficient on large datasets.
- **Bubble Sort** is easy to implement but inefficient for large arrays.

---

###  Challenges

- Accurate step counting in nested loops.
- Debugging logic in sorting steps and conditions.

---

###  Conclusion

Basic understanding of algorithm complexities is crucial for designing efficient software. Choosing the right algorithm significantly impacts performance.




