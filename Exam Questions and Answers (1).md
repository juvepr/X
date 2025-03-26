# Exam 2 Conceptual Practice - Questions and Answers

## Question 1
**What is a potential drawback of using recursion without memoization for solving certain problems?**
- Correct Answer: It may involve redundant calculations and increased runtime

## Question 2
**Compared to recursive solutions, iterative solutions tend to...**
- Correct Answer: Use less memory

## Question 3
**Which statement best describes greedy algorithms?**
- Correct Answer: When choosing between multiple paths, they tend to take the path that brings them closest to the solution

## Question 4
**Memoization is a technique used to:**
- Correct Answer: Store and reuse solutions to overlapping subproblems

## Question 5
**How does memoization help in optimizing algorithms?**
- Correct Answer: By storing previously computed results to avoid redundant calculations

## Question 6
**What is the output of the following Fibonacci code?**
```python
def Fibonacci(n):
    if n == 0: 
       return 0
    elif n == 1: 
       return 1
    else: 
       return Fibonacci(n-1) + Fibonacci(n-2)
 
print(Fibonacci(5))
```
- Correct Answer: 5

## Question 7
**What is the output of the following recursive function?**
```python
def recursive_function(n):
    if n == 0:
        return 0
    return n + recursive_function(n)
 
result = recursive_function(5)
print(result)
```
- Correct Answer: Raises a RecursionError

## Question 8
**When dynamic programming is applied to a problem, it takes far less time as compared to other methods that don't take advantage of overlapping subproblems.**
- Correct Answer: True

## Question 9
**Recursion is similar to which of the following?**
- Correct Answer: Loop

## Question 10
**Greedy algorithms always give an optimal solution.**
- Correct Answer: False

## Question 11
**Fewest Coins Problem (first implementation)**
- Correct Answers: 
  - n1: 3
  - n2: 3

## Question 12
**Fewest Coins Problem (second implementation)**
- Correct Answers:
  - n1: 3
  - n2: 2

## Question 13
**Fewest Coins Problem (third implementation)**
- Correct Answers:
  - n1: 3
  - n2: 2

## Question 14
**Recursive Random Number Generation (Debugger Question)**
- Incorrect/Skipped

## Question 15
**Matching: Sorting Algorithm Terms**
- Adaptive: The algorithm is asymptotically better on some partially sorted inputs
- In-Place: The algorithm uses O(1) memory overhead
- Stable: The ordering of equal items is preserved while sorting

## Question 16
**Binary Search Requirement**
- Correct Answer: The list must be sorted

## Question 17
**Binary Search Middle Element Role**
- Correct Answer: It is compared with the target element and used to divide the search space in half

## Question 18
**Binary Search Recursive with Slicing Time Complexity**
- Correct Answer: O(n)

## Question 19
**Binary Search Recursive with Indices Time Complexity**
- Correct Answer: O(logn)

## Question 20
**Sorting Algorithm Write Operations**
- Correct Answer: Selectionsort

## Question 21
**Sorting Algorithm List Progression**
- Bubblesort progression explained
- Insertionsort progression explained
- Selectionsort progression explained
- Cocktailsort progression explained

## Question 22
**Sorting Algorithm Final Position Guarantee**
- Correct Answer: Cocktailsort

## Question 23
**Adaptive Sorting Algorithms**
- Correct Answers: Bubblesort, Insertionsort

## Question 24
**In-Place Sorting Algorithms**
- Correct Answers: Bubble sort, Selection sort, Insertion sort

## Question 25
**Stable Sorting Algorithms**
- Correct Answers: Bubble sort, Insertion sort

## Question 26
**Binary Search Time Complexity**
- Best Case: O(1)
- Worst Case: O(logn)
- Average Case: O(logn)

## Question 27 & 34
**Quadratic Sorting Algorithms Time Complexity**
- Bubblesort: 
  - Best: O(n)
  - Worst: O(n^2)
  - Average: O(n^2)
- Selectionsort:
  - Best: O(n^2)
  - Worst: O(n^2)
  - Average: O(n^2)
- Insertionsort:
  - Best: O(n)
  - Worst: O(n^2)
  - Average: O(n^2)

## Question 28
**Divide-and-Conquer Algorithm Characteristics**
- They break a large problem into independent subproblems
- They have elegant recursive solutions
- They can be sped up with parallelization

## Question 29
**Linearly Adaptive Sorting Algorithms**
- Correct Answers: Bubblesort, Insertionsort

## Question 30
**Fewest Write Operations Sorting Algorithm**
- Correct Answer: Selectionsort

## Question 31
**Fastest Sorting Algorithm for Large Randomized List**
- Correct Answer: Quicksort

## Question 32
**Divide and Conquer Algorithm**
- Correct Answer: Mergesort

## Question 33
**Merging Two Sorted Lists Comparison Complexity**
- Correct Answer: O(m+n)

## Question 35
**Mergesort Time Complexity**
- Best: O(nlogn)
- Worst: O(nlogn)
- Average: O(nlogn)

## Question 36
**Quicksort Time Complexity**
- Best: O(nlogn)
- Worst: O(n^2)
- Average: O(nlogn)

## Question 37
**Quicksort Pivot Selection**
- Correct Answer: The median value of the current sublist
