# Design and Analysis of Algorithms
[Midterm](#midterm)
<br>
[Final](#final)
<br>
[Interview Questions](#intQ
<br>

<a name="midterm"></a>
## Midterm Review

<a name="intQ"></a>
## Interview Questions
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
