Add your answers to the Algorithms exercises here.

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```
a)  a = 0
    while (a < n * n * n):
      a = a + n * n
```
Since a is increasing by n^2 each time through the loop, and we are iterating until we reach n^3, it will take us n^3 / n^2 passes before our while condition is no longer true.  Thus, this code will have a runtime complexity of O(n).


```
b)  sum = 0
    for i in range(n):
      i += 1
      for j in range(i + 1, n):
        j += 1
        for k in range(j + 1, n):
          k += 1
          for l in range(k + 1, 10 + k):
            l += 1
            sum += 1
```
The i, j, k loops will all have a runtime complexity of O(n).  Since they are nested this will lead to O(n^3).  The l loop only runs 9 times: (10 + k) - (1+k).  This is negligible for large values of n, so the entire algorithm will have a runtime complexity of O(n^3).



```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```
Considering the input `bunnies` to be n, there will be n-1 recursive calls before we reach the base case.  There is no other logic in the function that will take any time on each pass until the base case is hit.  Thus this algorith has a runtime complexity of O(n).

## Exercise II

Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode and give the runtime complexity of your solution.


## Answer
This is simply a binary search.

while length of building > 1 floor:
  find midpoint of building
  drop egg
  if breaks:
    new building starts at old bottom and ends at current midpoint
  if not breaks:
    new building starts at current midpoint and ends at old top
