# Apriori Algorithm Implementation 🛒🔍

This repository contains a Python implementation of the Apriori algorithm for discovering frequent itemsets in transaction data and generating association rules.

## Features
- Efficiently identifies frequent itemsets and generates association rules.
- Handles large transaction datasets using candidate generation and pruning strategies.
- Simple implementation in a single Python script.

## Usage
1. **Run `apriori.py`**: Modify `transactions` and `min_support` parameters to analyze different transaction datasets.

## Example
```python
# Example transaction data
transactions = [
    ['apple', 'banana', 'cherry'],
    ['banana', 'orange'],
    ['apple', 'banana', 'orange'],
    ['apple', 'cherry'],
    ['apple']
]

min_support = 3

frequent_itemsets = apriori(transactions, min_support)
print("Frequent Itemsets:")
print(frequent_itemsets)
