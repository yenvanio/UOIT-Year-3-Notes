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
  - The terminating condition is when j > length of array and when it becomes n+1 the array consists of values A[1..n], all sorted

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
- Programs that call themselves to solve a problem
- Follows a divde and conquer method
  - Breaks down problem into several subproblems
  - Solve each subproblem recursively
  - Combine solutions together to form solution to original problem

### Merge Sort
- **Divide**: Divide n-element sequence in half (n/2) to be sorted
- **Conquer**: Sort the two subsequences recursively using merge sort
- **Combine**: merge the two sorted subsequences to get full sorted list
- Runtime = O(nlogn)

```Java

MERGE_SORT(A,p,r)
  (if p < r){
    q = Math.Floor((p+r)/2);
    MERGE_SORT(A, p, q);
    MERGE_SORT(A, q+1, r);
    MERGE_SORT(A, p, q, r);
  }

```

  **Note**: Basically divide by 2 until single elements and join back same way while sorting by checking the first element of each subsequence to find the smallest number to put into final answer first

#### Correctness of Merge Algorithm
- Need to check
  - Initialization  
    - Before first loop iteration empty subarray
  - Maintenance
    - Once broken down into single elements you check smallest element in left side vs right side and smaller one goes into final array. Once the subsequences get bigger you go through each index of subsequences cause they're sorted and make sure the left and right side combine properly
  - Termination
    - Upon termination the subarray is already sorted *except for two largest elements which are sentinnels*??

### Divide and Conquer Algorithms
- *a*: Number of subproblems, each one is 1/b * size of the original problem
- *T(n/b)*: Time required to solve one subproblem of size n/b
- *D(n)*: Time required to divide problem into subproblems
- *C(n)*: Time required to combine subsolutions into main solution
- T(n) = { O(1)                   if n <= c
           aT(n/b) + D(n) + C(n)  otherwise  
                                            }

```

Ex for Merge Sort Algorithm:

T(n) = { O(1)           if n = 1
         2T(n/2) + O(n) if n > 1
                                 }

*Note* D(n) = O(1) because divide step only computes middle of subarray which takes constant time.

The MERGE procedure takes O(n) on an n-element subarray and so combined we get the answer above

```

### Big O, Omega, Theta
- Big O is an asymptotic upper bound for a function
- Big Omega is an asymptotic lower bound for a function
- Big Theta is an upper and lower bound (sandwiched)

- Big O and Omega have to be true for a function for a function to be Big Omega
  - Similarly if a function is Big Theta, it is also O and Omega
- If f(n) = Big Theta/Omega/O g(n) && g(n) = Big Theta/Omega/O h(n)
  - Then f(n) = Big Theta/Omega/O(h(n))

### Function Notations
- f(n) is **monotonically increasing** if *m <= n* implies *f(m) <= f(n)*
- f(n) is **monotonically decreasing** if *m <= n* implies *f(m) >= f(n)*
- f(n) is **strictly increasing** if *m < n* implies *f(m) < f(n)*
- f(n) is **strictly decreasing** if *m < n* implies *f(m) > f(n)*

#### Floor and Ceiling
- Floor of # = Round down
- Ceiling of # = Round up

```
Ceiling of ((x/a)/b) = Ceiling of (x/ab)
Floor of ((x/a)/b) = Floor of (x/ab)

Ceiling of (a/b) = Ceiling of (( a + (b-1) ) / b )
Floor of (a/b) = Floor of (( a + (b-1) ) / b )

```

- Both functions are **monotonically increasing**


### Solving Recurrences
- For complicated ones, can use dummy variables in sub back in later
- Substitution
  - For different values of k, substitute the function T to solve for a general form
  - Ex: Merge Sort

  ```
  Find Time Complexity of: T(n) = 2T(n/2) + n
  * 2T because divide by 2 each time
  * n/2 because n/2 subproblems
  * n because linear operations of dividing and combining

  First set k = 1   (k is the exponent on the T)
  T(n) = 2T(n/2) + n

  Then find T(n/2) by subbing n/2 into original function
  T(n/2) = 2T(n/4) + n/2

  Now sub T(n/2) back into the first function to get function for k=2
  T(n) = 2( 2T(n/4) + n/2 ) + n
  T(n) = 2^2T(n/4) + 2n

  Repeat for k=3 to get
  2^3T(n/8) + 3n

  Pattern is -> T(n) = (2^k)T(n/2^k) + kn

  Now declaring base case T(1) = 1
  so want to do recursion back to base case otherwise infinite loop
  SO.. n/2^k = 1
  n = 2^k
  k = logn (base 2)

  Sub back in for k ((Since logn is base 2 and being raised to the power of 2 can switch the bottom 2 with top n)
  T(n) = 2^logn * T(1) + log(n)*n
  T(n) = n^log2 * T(1) + nlogn
  T(n) = n * T(1) + nlogn
  T(n) = nlogn

  ```

- Recursion Tree Method
  - Each node in the tree represents cost of a subproblem
  - Sum the costs within each level to get a set of per-level costs and sum them all to get
  total cost of the recursion
  - Width of tree -> a^log_b_n = n^log_b_a
  - Depth of tree -> log_b_n
  - Ex:

  ```
  T(n) = 3T(n/4) + cn^2

  The constant on the side is the head of the three and should be the row sum for every level(
  Each node should break down into 3 parts (coefficient of T)
  Each level lower, the breakdown into 3 nodes should be multiplied by the coefficient of n/4 (1/4) (So in this case denominator keeps x4)
  Each level you go down you will notice a pattern for the recursive call T(n/4^i) (basically the x1/4 thing mentioned above)
  Want that to equal 1 for base case -> 1 = n/4^i
                                     -> log_4_n = i
  Now to calculate final time complexity, take the log_4_n = i and mutliply it by the row sum
  log(n)*n^2 = n^2logn = n^2 time complexity


  ```

- Master Method


--------------------------------------------------
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
