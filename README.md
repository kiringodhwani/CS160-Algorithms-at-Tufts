**Assignment:**
**1. Dynamic Programming:** Implement a solution to the below dynamic programming problem. First implement a solution using a top-down approach (making recursive calls and storing “memos”), and then implement a solution using the bottom-up method (filling in a table with a for-loop instead of recursive calls).
  - There is a dragon with exactly n health. Find the minimum number of magical stones needed to inflict exactly n damage, as to not tire our adventurer. Stones are each associated with a fixed amount of damage it inflicts, and you are able to select a stone as many times as you want. The stone damages are given to you in an array. You can assume there always exists a set of stones that can kill the dragon. 
  - In the first section of my program, you can find both the top-down and bottom-up approaches for solving this problem.


**2. Two-Finger Algorithm:**
  - Given an array of distinct numbers, define a flip to be a pair of numbers such that the smaller one is to the right of the larger one. For example, in the array [3, 2, 1], there are three flips: (3, 2), (3, 1), and (2, 1). The array [1, 2, 3] has zero flips. Provide an algorithm that finds the number of flips in any permutation of n numbers. It must run in Θ(n log n) time.
  - To solve this problem, I used a two-finger algorithm / modified version of MergeSort. See the second section of my program to view said solution.


