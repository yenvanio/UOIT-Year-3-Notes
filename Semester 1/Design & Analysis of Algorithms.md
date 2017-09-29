# Design and Analysis of Algorithms

## Lecture 2

#### TSP - Travelling Salesman Problem
- Most popular combinatorial problem
- Family of optimization problems
- Solve one you can solve all
  - Find Hamiltonian Cycle for a country
  - N, number of cities = N! possibilities using brute force

#### Parallelism
- To increase speed, parallel processing
- Several processing cores

#### Algorithms and Technology
- Explicit Use: Algorithms used at application level
- Implicit Use: Algorithms used in design process
- Examples:
  - Fast Hardware: Use software to design hardware (implicit)
  - GUI: explicit use of algorithm

#### Insertion Sort
- _Note: In textbook examples, all indices start from 1_
- In place sorting algorithm
- Procedure
  - N = 2
  - Start at Nth Element __(For Loop)__
  - Check Nth Element with all elements before it __(While Loop)__
  - Swap smaller elements with larger ones

#### Loop Invariants
- White Box Technique
- __Initialization:__ It is true prior to first iteration of loop
  - Shows Array is sorted when j = 2 (initializing) the only item in the array is Array[1]
- __Maintenance:__ If true before iteration, it is true after
  - After every iteration the values are moved until right position is found and then it is inserted, so still sorted.
- __Termination:__ When loop terminates, invariant gives us a useful property that helps show algorithm is correct
  - The terminating condition is when j > length of array and when it becomes n+1 the array consists of values A[1..n],
  all sorted

#### Mathematical Induction vs Loop Invariants
- Base Case = Initialization
- Inductive Step = Maintenance
- Inductive Step Infinitely != Termination

#### Best Case, Average Case, Worst Case
- Best case is when the array is already sorted
  - Should never have to go through while loop (to check with all elements before it)
  - Because already sorted
- Average would be half sorted and half unsorted
- Worst case is when the array is sorted in reverse
  - Will always go through the whole while loop (n-1 times)
  - Because have to bring elements from last index to first index
- Usually focus on worst case, because that is the longest time it will ever take to run the algorithm, so we want to focus on making it smaller

## Lecture 7

#### Interview Question
You have a set of date intervals represented by StartDate and EndDate. How would you efficiently calculate the longest timespan covered by them?

What is Time Complexity?

```
Set of End Dates && Set of Start Dates

Time Complexity = O(NlogN)

Sort intervals by start date.
Take first interval as actual range.
Loop over intervals and if the current
StartDate is within the actual range,
extend EndDate of the actual range if
needed and extend maximal timespan
achieved so far if needed. Otherwise,
use current interval as new actual
range. Time Complexity is O(N)

```

#### Divide and Conquer Algorithm
