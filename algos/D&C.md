# divide and conquer (分數形名)

> 凡治眾如治寡，分數是也。鬥眾如鬥寡，形名是也。

- divide problem til easy to solve, then combine results
- sub-problems are divided from original problem, combine results of sub-problems can get result of original problem
- sub-problem should maintain same form while dividing, only problem size decrease

## premise

- problem can be separated into independent parts
- there is no dependency between different parts of the problem

## flow

1. split original problem
2. solve sub-problems recursively
3. combine solutions into overall solution

## to design a D&C algo

0. clarify objective
   - What to find?
   - What should the result be? (nature instead of value)
   - How to determine if an optimal result is found?
1. decide how the problem should be divided
   - independent (in terms of the problem and the solution)
   - number of sub-problems
   - size of sub-problem
2. decide the conquer part
   > how to solve the problem on one step (i.e. on each step)
   - it is correct for each step (regarding the objective)
   - clarify condition to maintain for ensuring each step is correct
3. ensure base case can be solved correctly

## example

### merge sort

1. keep splitting list into 2 halves

   > O(log(n))

2. return when size is 1

3. merging results of 2 halves following order

   > O(n)

overall complexity: O(log(n)\*n)=O(nlog(n))
