# CMPS 6610 Problem Set 04
## Answers

**Name:**Adam Ledet


Place all written answers from `problemset-04.md` here for easier grading.




- **1d.**

File        | Fixed-Length Coding   |   Huffman Coding    | Huffman vs. Fixed-Length
----------------------------------------------------------------------
f1.txt      |           1340        |           826     |       0.616418
alice29.txt |           1039367     |           676374  |       0.650756
asyoulik.txt|           876253      |           606448  |       0.692092
grammar.lsp |           26047       |           17356   |       0.666334
fields.c    |           78050       |           56206   |       0.720128

Huffman coding is consistently smaller than fixed-length encoding by a facor of between ~30 and 40%.


- **1d.**
When Huffman encoding for any alphabet where all characters appear equally, Huffman encoding will always be as good or better than fixed length encoding depending on how close the length of sigma is to a power of 2. If the length of sigma is a power of 2, it will be identical to the fixed-length cost. If the length of sigma is slightly greater than a power fo 2, huffman encoding will be greatly better; and if the length of sigma is slightly less than a power of 2, Huffman encoding will only be slightly better.




- **2a.**
Let us translate our array of A elements into a binary tree with the heap property by making our first term our root and the next two terms being its children and follosing terms being their children such that [6, 5, 4, 3, 2, 1] would be a tree with 6 as the root and 5 and 4 its children and 3 and 2 the children of 5 and 1 the child of 4. Begin at the bottom-left most node of our tree and compare it to its parent. If the child is less than its parent, swap the two. Compare the same parent node with its other child and then move up the tree until every parent node has been compared with its children at that level of the tree and then move to the left-most parent node of the next level.
In the example, we would begin with 3 and compare it to its parent, 5. They would swap, and then we would compare 3 with its other child, 2 (and they would swap again such that 2 is the parent of 3 and 5).



- **2b.**
The span of this algorithm is O(n) because we are, in the worst case, making a comparison a number of times equal to the number of entries in our tree as we compare parents with each of their children.



- **3a.**
Take 1 of the largest coin that is smaller than the remaining change needed. Repeat this until no more change is needed.


- **3b.**
Greedy Choice Proof: For any amount of change, assume there is a way to make change without our greedy choice. This means that the sum of some non-greedy denominations equals the amount of our greedy choice because all our denominations are powers of 2. Because our greedy choice is greater than any other (by our choice's definition), we can make our solution without using the greedy choice more optimal by including the greedy choice and replacing terms that add up to the greedy choice's value with the greedy choice. EX: Making 25 with 8, 8, 8, 1 can be made more optimal by replacing two 8s with a 16 greedy choice.
Optimal Substructure Proof: For any amount of change, there will be an optimal number of coins to make change.


- **3c.**
Our work and span are *O*(logn) because you will be reducing your problem by a power of 2 at each step and will take no more steps than the log_2 of the problem size.


- **4a.**
Because it is possible to be unable to make change, the largest coin smaller than remaining change is not guaranteed to be a part of the answer and therefore cannot be a greedy choice. As an example, assume there is a denomination one less than the change needed, but there is no denomination for 1. If there is a correct way to give change by using two smaller denominations, the above algorithm is not optimal.
EX: Need 5 change. Change bills are 2s, 3s, and 4s. The above algorithm would pick a 4 and be unable to make proper change when change can be gathered with a 2 and 3.



- **4b.**
While we do not know a denomination is in our optimal solution (which would prove the greedy property), we do know that smaller values of optimal change can be put together to form the optimal solution for the whole. If we reduce our problem, we are left with a problem that has an optimal solution (or no solution).
Our subproblem will be removing a denomination from our change and taking the minimum number of coins from all of the results.
EX: need 5 change. Change bills are 2s, 3s, and 4s. We check if we have the exact right change; and, if not, break it into three sumproblems of change for 3, 2, and 1. We don't have a bill for 1 (meaning 4 is out), but we do have a perfect match for 3 and 2; they are both the minimum and are optimal solitions.



- **4c.**
Let us reduce our problem by removing one denomination of each possible type from our problem. Continue to do so until we either cannot create change or make perfect change. Then, collect the number of coins needed for each breakdown and take the minimum of these results. This approach will give you an acyclic binary tree.
Our work is *O*(kn) where k is the number of denominations and n is the size of our input. Our span is *O*(n) as we need to perform our calculation at most a number of times to get our input from itself to 0 decreasing by a minimum (assuming only integer denominations).


- **5a.**
This does have an optimal substructure. The optimal structure of a section of time will contain sections of optimal non-overlapping tasks.


- **5b.**
This problem does not have the Greedy property.
Use the Greedy criteria to select the most valuable task: It is possible that selecting the most valuable task interferes with two or more tasks whose combined value exceeds it.
Use the Greedy criteris to select the task with the best time/value ratio: Similar to above, it is possible that this conflicts with two different tasks that, combined, have a value (and possibly even time value) that are better.



- **5c.**
Reduce the problem into all tasks that conflict with the first task making a new tree branch for each. On each branch, repeat for the next subsequent task. Once there are no more tasks for a branch of the tree, record the total value and take the maximum across all branches.
Our work and span are *O*(n) because we are calling every scheduled task combination once. In a worst-case scenario, we have n leaves (all the tasks conflict) or a tree that is n long (none of them conflict).
Assuming we need to sort our tasks from our first starting task start time to our last starting task's start time, this can be done in *O*(nlogn) time which dominates our algorithm, meaning the entirety of our algorithm is done in *O*(nlogn) time.