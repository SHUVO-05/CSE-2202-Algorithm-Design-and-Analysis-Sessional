# Lab 05: Dynamic Programming – Fibonacci and 0/1 Knapsack Problem

## I. Learning Objectives
- Understand dynamic programming (DP) paradigm.
- Implement Fibonacci using memoization (top-down DP).
- Solve the 0/1 Knapsack problem using DP.
- Analyze time and space complexity.

---

## Experiment 1: Fibonacci Number using Memoization

### Algorithm Complexity
- Time Complexity: O(n)
- Space Complexity: O(n) for memoization array and recursion stack.

---

### Source Code (C++)
```cpp
// Fibonacci
#include <iostream>
using namespace std;

int fib(int n, int memo[]) {
    if (n <= 1)
        return n;
    if (memo[n] != -1)
        return memo[n];
    memo[n] = fib(n - 1, memo) + fib(n - 2, memo);
    return memo[n];
}

int main() {
    int n;
    cout << "Enter n: ";
    cin >> n;

    int memo[n + 1];
    for (int i = 0; i <= n; i++)
        memo[i] = -1;

    cout << "Fibonacci number is: " << fib(n, memo) << endl;
    return 0;
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2005/Fibonacci.png)


# Experiment 2: 0/1 Knapsack Problem

## Problem Statement
Given weights and values of n items, put these items in a knapsack of capacity W to get the maximum total value without exceeding the capacity.

---

## Algorithm Complexity
- Time Complexity: O(nW)
- Space Complexity: O(nW)

---

## Source Code (C++)
```cpp
// 0/1 Knapsack Problem
#include <iostream>
#include <vector>
using namespace std;

int knapsack(int W, vector<int> wt, vector<int> val, int n) {
    int dp[n + 1][W + 1];

    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0)
                dp[i][w] = 0;
            else if (wt[i - 1] <= w)
                dp[i][w] = max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w]);
            else
                dp[i][w] = dp[i - 1][w];
        }
    }
    return dp[n][W];
}

int main() {
    int n, W;
    cout << "Enter number of items: ";
    cin >> n;

    vector<int> val(n), wt(n);
    cout << "Enter values: ";
    for (int i = 0; i < n; i++)
        cin >> val[i];

    cout << "Enter weights: ";
    for (int i = 0; i < n; i++)
        cin >> wt[i];

    cout << "Enter knapsack capacity: ";
    cin >> W;

    cout << "Maximum value in Knapsack = " << knapsack(W, wt, val, n) << endl;

    return 0;
}
```
### Sample Output

![Linear Search Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2005/Knapsack.png)
