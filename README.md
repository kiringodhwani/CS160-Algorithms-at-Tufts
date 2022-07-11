**Assignment:**

**1. Dynamic Programming:** Implement a solution to the below dynamic programming problem. First implement a solution using a top-down approach (making recursive calls and storing “memos”), and then implement a solution using the bottom-up method (filling in a table with a for-loop instead of recursive calls).
  - **Problem:** There is a dragon with exactly n health. Find the minimum number of magical stones needed to inflict exactly n damage. Stones are each associated with a fixed amount of damage it inflicts, and one is able to select a stone as many times as they want. The stone damages are given in an array. One can assume there always exists a set of stones that can kill the dragon. 
  - **Solution:** In the 1st section of my program, you can find both the top-down and bottom-up solutions.


**2. Two-Finger Algorithm:**
  - **Problem:** Given an array of distinct numbers, define a flip to be a pair of numbers such that the smaller one is to the right of the larger one. For example, in the array [3, 2, 1], there are three flips: (3, 2), (3, 1), and (2, 1). The array [1, 2, 3] has zero flips. Provide an algorithm that finds the number of flips in any permutation of n numbers. It must run in Θ(n log n) time.
  - **Solution:** To solve this problem, I used a two-finger algorithm / modified version of MergeSort. In the 2nd section of my program, you can find said solution.


