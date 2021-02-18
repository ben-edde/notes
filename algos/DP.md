# dynamic programming
  
> Those who cannot remember the past are condemned to repeat it.  

## idea  

- divide a problem into smaller overlapping sub-problems, then combine results
    > as subproblem is part of original problem, result of sub-problems can form solution to original problem
- sub-problem should maintain same form while dividing, only problem size decrease
- solutions of sub-problems are memorized  
    > as sub-problems are overlapping, same problem can appear for multiple times, solving same problems repeatedly wasting resources

## difference from D&C

- some problems cannot be split into independent sub-problems, for these problem DP is needed

## flow  

1. split the original problem  
2. solve sub-problems with help of common memory  
3. combine solutions into solution to original problem

## to design a DP algo

## example
