# Lab 03: Divide and Conquer – Quick Sort (Recursive & Iterative)

##  Learning Objectives
- Implement Quick Sort (recursive & iterative).
- Compare their complexities and performance.

---

##  Experiment 1: Recursive Quick Sort

###  Time Complexity
- Average: `O(n log n)`
- Worst: `O(n²)`

###  Space Complexity
- `O(log n)` (due to recursion stack)

###  Source Code (C++)

```cpp
// Recursive Quick Sort
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for(int j = low; j < high; j++) {
        if(arr[j] <= pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i+1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if(low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi -1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr)/sizeof(arr[0]);
    
    quickSort(arr, 0, n-1);
    
    cout << "Sorted array: ";
    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
    
    return 0;
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2003/Recursive%20Quick%20Sort.png)
# Experiment 2: Iterative Quick Sort

## Time Complexity
- Average: O(n log n)  
- Worst: O(n²)

## Space Complexity
- O(n) due to explicit stack

---

## Source Code (C++)
```cpp
// Iterative Quick Sort
#include <iostream>
#include <stack>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for(int j = low; j < high; j++) {
        if(arr[j] <= pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i+1], arr[high]);
    return i + 1;
}

void iterativeQuickSort(int arr[], int low, int high) {
    stack<int> stack;
    stack.push(low);
    stack.push(high);
    
    while(!stack.empty()) {
        high = stack.top(); stack.pop();
        low = stack.top(); stack.pop();
        
        int pi = partition(arr, low, high);
        
        if(pi - 1 > low) {
            stack.push(low);
            stack.push(pi - 1);
        }
        if(pi + 1 < high) {
            stack.push(pi + 1);
            stack.push(high);
        }
    }
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr)/sizeof(arr[0]);
    
    iterativeQuickSort(arr, 0, n-1);
    
    cout << "Sorted array: ";
    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
    
    return 0;
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2003/Iterative%20Quick%20Sort.png)
# Analysis Table (Lab 2 & 3)

| Algorithm     | Best Case   | Worst Case | Average Case | Space Complexity                    |
|---------------|-------------|------------|--------------|-----------------------------------|
| Merge Sort    | O(n log n)  | O(n log n) | O(n log n)   | O(n)                              |
| Quick Sort    | O(n log n)  | O(n²)      | O(n log n)   | O(log n) recursive, O(n) iterative|
| Binary Search | O(1)        | O(log n)   | O(log n)     | O(1) iterative, O(log n) recursive|

---

# Observations

- Merge Sort guarantees O(n log n) time but requires extra space.
- Quick Sort is generally faster but worst case is O(n²).
- Recursive and iterative versions of algorithms differ mainly in space usage.

---

# Challenges

- Managing recursion and stack overflow in large inputs.
- Correctly implementing iterative versions with explicit stacks.

---

# Conclusion

Divide and Conquer techniques enable efficient algorithms for large datasets through recursion and problem splitting.
