# Design and Analysis of Algorithms
[Midterm](#midterm)
<br>
[Final](#final)
<br>
[Interview Questions](#intQ)
<br>

<a name="midterm"></a>
## Midterm Notes

### Insertion Sort
- An in place sorting algorithm
- Efficient for small number of elements

```
for j = 2 to A.length                                   c1    n
  key = A[j]                                            c2    n-1
  // Insert A[j] into the sorted sequence A[1...j-1]    
  i = j - 1                                             c4    n-1
  while i > 0 and A[i] > key                            c5    sum of operations tj from j -> n
    A[i + 1] = A[i]                                     c6    sum of operations tj-1 from j -> n
    i = i - 1                                           c7    sum of operations tj-1 from j -> n
  A[i + 1] = key                                        c8    n - 1

  T(n) = c1n + c2(n-1) + c4(n-1) + c5(sum of tj) + c6(sum of tj - 1) + c7(sum of tj - 1) + c8(n-1)
  T(n) = an + b
  ** Which is a linear function **

```
- Steps
  - Basically for loop to go through all the elements
  - Start at index+1 and check with the number before it
    - While smaller, keep going to find correct position
    - With each check, if smaller you swap


### Loop Invariants
    - White Box Technique
    - __Initialization:__ It is true prior to first iteration of loop
      - Shows Array is sorted when j = 2 (initializing) the only item in the array is Array[1]
    - __Maintenance:__ If true before iteration, it is true after
      - After every iteration the values are moved until right position is found and then it is inserted, so still sorted.
    - __Termination:__ When loop terminates, invariant gives us a useful property that helps show algorithm is correct
      - The terminating condition is when j > length of array and when it becomes n+1 the array consists of values A[1..n],
      all sorted

### Mathematical Induction vs Loop Invariants
    - Base Case = Initialization
    - Inductive Step = Maintenance
    - Inductive Step Infinitely != Termination

### Best Case, Average Case, Worst Case
    - Best case is when the array is already sorted
      - Should never have to go through while loop (to check with all elements before it)
      - Because already sorted
    - Average would be half sorted and half unsorted
    - Worst case is when the array is sorted in reverse
      - Will always go through the whole while loop (n-1 times)
      - Because have to bring elements from last index to first index
    - Usually focus on worst case, because that is the longest time it will ever take to run the algorithm, so we want to focus on making it smaller

### Recursion

<a name="intQ"></a>
## Interview Questions
1. You have a set of date intervals represented by StartDate and EndDate. How would you efficiently calculate the longest timespan covered by them?

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
