# Algorithms Cheat Sheet

## 1. Fewest Coins (Recursive with Memoization)
```python
def fewestcoins_recr(amt, coins):
    """Recursive, but uses memoization to avoid redundant solutions"""
    solved = {coin: 1 for coin in coins}  # can make any amt in coins w/ 1 coin
    return _fewest_coins_memo(amt, coins, solved)

def _fewest_coins_memo(amt, coins, solved):
    """Helper function for memoized coin counting"""
    # Base case - already solved this
    if amt in solved:
        return solved[amt]

    # Otherwise, start guess at infinity
    solved[amt] = float('inf')

    # explore every branch from here, find minimum
    for coin in coins:
        if coin < amt:
            n_coins_branch = 1 + _fewest_coins_memo(amt-coin, coins, solved)
            if n_coins_branch < solved[amt]:
                solved[amt] = n_coins_branch

    # we've found the optimal for amt - return it
    return solved[amt]
```

## 2. Binary Search (Recursive)
```python
def binary_search_recr(L, item):
    """Returns True iff item is in L"""
    return _binarysearch(L, item, idx_left=0, idx_right=len(L))

def _binarysearch(L, item, idx_left, idx_right):
    """Helper function for recursive binary search"""
    # Base case - empty sublist
    if idx_right - idx_left == 0:
        return False

    # Find median
    idx_med = (idx_right + idx_left) // 2
    item_med = L[idx_med]

    if item == item_med:
        return True
    elif item < item_med:
        return _binarysearch(L, item, idx_left=idx_left, idx_right=idx_med)
    else:
        return _binarysearch(L, item, idx_left=idx_med+1, idx_right=idx_right)
```

## 3. Binary Search Index (Recursive)
```python
def bs_index(item, L):
    """Returns the index of the first appearance of item in L"""
    return _bs_index(item, L, left=0, right=len(L), i_first=None)

def _bs_index(item, L, left, right, i_first):
    """Helper function to recursively find first occurrence of item"""
    # Base case - empty sublist
    if right - left == 0:
        return i_first

    # Update guess of first occurrence
    if L[left] == item:
        i_first = left

    # Base case - sublist of 1 item
    if right - left == 1:
        return i_first

    # Recursive case - keep searching
    median = (right + left) // 2

    if L[median] > item:
        return _bs_index(item, L, left, median, i_first)
    elif L[median] < item:
        return _bs_index(item, L, median, right, i_first)
    elif left != median:
        i_first = median
        return _bs_index(item, L, left, median, i_first)
```

## 4. Greatest Common Divisor (Recursive)
```python
def gcd(a, b):
    """Recursively calculates the greatest common divisor (GCD) using Euclid's algorithm"""
    if b == 0:
        return a
    return gcd(b, a % b)
```

## 5. Factorial (Recursive)
```python
def factorial(n):
    """Recursively calculates the factorial of a given non-negative integer n"""
    if n == 1:
        return 1
    return n * factorial(n - 1)
```

## 6. Count Digits (Recursive)
```python
def count_digits(n):
    """Recursively counts the number of digits in an integer"""
    if n < 10:
        return 1
    return 1 + count_digits(n // 10)
```

## 7. Bubble Sort (Adaptive)
```python
def bubblesort(L):
    """Sorts L using bubblesort with optimizations"""
    n = len(L)
    for i in range(n-1):
        made_swaps = False

        # bubble items up
        for j in range(n-1-i):
            if L[j] > L[j+1]:
                made_swaps = True
                L[j], L[j+1] = L[j+1], L[j]

        # short circuit if finished
        if not made_swaps:
            return L
    return L
```

## 8. Selection Sort
```python
def selectionsort(L):
    """Sorts L using selection sort"""
    n = len(L)

    for i in range(n-1):
        # Find the biggest item
        idx_max = 0
        item_max = L[idx_max]

        for j in range(n-i):
            if L[j] > item_max:
                idx_max = j
                item_max = L[idx_max]

        # swap the biggest to the end of this sublist
        L[j], L[idx_max] = L[idx_max], L[j]
    return L
```

## 9. Insertion Sort
```python
def insertionsort(L):
    """Sorts L using insertion sort"""
    n = len(L)

    for i in range(n-1):
        # Extract next item to be sorted
        j = n-2-i
        item = L[j]

        # Shift everything smaller one left
        while j < n-1 and item > L[j+1]:
            L[j] = L[j+1]
            j += 1

        # write item to its new position
        L[j] = item
    return L
```

## 10. Merge Sort
```python
def mergesort(L):
    """Recursively sorts list using merge sort"""
    if len(L) <= 1:
        return L  # base case: List is trivially sorted if empty or 1 item

    i_median = len(L) // 2
    L_left = mergesort(L[:i_median])  # merge_sort() eventually returns sorted left half
    L_right = mergesort(L[i_median:])  # merge_sort() eventually returns sorted right half

    merge(L, L_left, L_right)  # List is now sorted in linear time
    return L

def merge(L, L_left, L_right):
    """Merges sorted lists L_left and L_right into L"""
    # Zip together until one list is fully written
    i, j = 0, 0
    while i < len(L_left) and j < len(L_right):
        if L_left[i] <= L_right[j]:
            L[i+j] = L_left[i]
            i += 1
        else:
            L[i+j] = L_right[j]
            j += 1

    # Write remaining items at the end of L
    L[i+j:] = L_left[i:] + L_right[j:]
```

## 11. Quick Sort (with Random Pivot)
```python
import random

def quickSort(L, left, right):
    """Recursively sorts list using quick sort with random pivot"""
    # Base case
    if right - left <= 1:
        return L

    # Divide
    pivot = partition(L, left, right)

    # Conquer
    quickSort(L, left, pivot)
    quickSort(L, pivot+1, right)

    # Combine: we're already doing in-place sorting
    return L

def partition(L, left, right):
    """Partitions the list around a randomly selected pivot"""
    # Select a random pivot and swap it with the last element
    pivot_index = random.randint(left, right - 1)
    L[pivot_index], L[right - 1] = L[right - 1], L[pivot_index]

    pivot = right - 1
    j = pivot - 1

    # Pivot all items between left and right
    while left < j:
        while left < j and L[left] < L[pivot]:
            left += 1
        while left < j and L[j] >= L[pivot]:
            j -= 1
        if left < j:
            L[left], L[j] = L[j], L[left]

    # Swap pivot and left if L[left] >= L[pivot]
    if L[left] >= L[pivot]:
        L[pivot], L[left] = L[left], L[pivot]
        pivot = left

    return pivot
```

## 12. Quick Select (with Random Pivot)
```python
import random

def QuickSelect(L, k, left, right):
    """Finds the kth smallest element in the list"""
    # Divide
    pivot = partition(L, left, right)

    # Base case
    if k == pivot + 1:
        return L[pivot]

    # Conquer
    elif k <= pivot:
        return QuickSelect(L, k, left, pivot)
    else:
        return QuickSelect(L, k, pivot + 1, right)

def partition(L, left, right):
    """Partitions the list around a randomly selected pivot"""
    # Select a random pivot and swap it with the last element
    pivot_index = random.randint(left, right - 1)
    L[pivot_index], L[right - 1] = L[right - 1], L[pivot_index]

    pivot = right - 1
    j = pivot - 1

    # Pivot all items between left and right
    while left < j:
        while left < j and L[left] < L[pivot]:
            left += 1
        while left < j and L[j] >= L[pivot]:
            j -= 1
        if left < j:
            L[left], L[j] = L[j], L[left]

    # Swap pivot and left if L[left] >= L[pivot]
    if L[left] >= L[pivot]:
        L[pivot], L[left] = L[left], L[pivot]
        pivot = left

    return pivot
```
