# Lab 04: Greedy Algorithms – Coin Change Problem

## Learning Objectives
- Understand the Greedy algorithm paradigm.
- Implement the Coin Change problem using a greedy approach.
- Analyze the time and space complexities.
- Compare greedy results with optimal solutions.

---

## Theory Recap
Greedy algorithms build up a solution piece by piece, always choosing the next piece that offers the most immediate benefit.

---

## Experiment: Coin Change Using Greedy Algorithm

### Problem Statement
Given a set of coin denominations, find the minimum number of coins that make a given amount.

### Algorithm Complexity
- **Time Complexity:** O(n), where n is the number of coin denominations.
- **Space Complexity:** O(1).

---

## Source Code (C++)
```cpp
// Coin Change Using Greedy Algorithm
#include <iostream>
#include <vector>
using namespace std;

void coinChangeGreedy(int amount, vector<int> coins) {
    vector<int> result;
    for (int coin : coins) {
        while (amount >= coin) {
            amount -= coin;
            result.push_back(coin);
        }
    }
    cout << "Coins used: ";
    for (int c : result) {
        cout << c << " ";
    }
    cout << endl;
}

int main() {
    vector<int> coins = {25, 10, 5, 1}; // Coins sorted in descending order
    int amount;
    cout << "Enter the amount: ";
    cin >> amount;

    coinChangeGreedy(amount, coins);
    return 0;
}
