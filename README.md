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

def apriori(transactions, min_support):
    frequent_itemsets = [[item] for item in set(item for transaction in transactions for item in transaction) if sum(1 for transaction in transactions if item in transaction) / len(transactions) >= min_support]

    k = 2
    while frequent_itemsets:
        candidates = [sorted(list(set(item) | {candidate})) for item in frequent_itemsets for candidate in set(transaction[k] for transaction in transactions if item[-1] in transaction) if candidate != item[-1]]
        candidate_counts = {tuple(candidate): sum(1 for transaction in transactions if set(candidate) <= set(transaction)) for candidate in candidates}
        frequent_itemsets = [list(candidate) for candidate, count in candidate_counts.items() if count / len(transactions) >= min_support]
        print('candidates:',candidates)
    return candidates

# Mining frequent itemsets
frequent_itemsets = apriori(transactions, min_support=0.4)
print("Frequent Itemsets:", frequent_itemsets)
