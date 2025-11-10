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
When Huffman encoding for any alphabet where all characters appear equally, Huffman encoding will always be smaller by an amount equal to double the alphabet's length.




- **2a.**




- **2b.**




- **3a.**
Take 1 of the largest coin that is smaller than the remaining change needed. Repeat this until no more change is needed.


- **3b.**



- **3c.**



- **4a.**
Because it is possible to be unable to make change, the largest coin smaller than remaining change is not guaranteed to be a part of the answer and therefore cannot be a greedy choice. As an example, assume there is a denomination one less than the change needed, but there is no denomination for 1. If there is a correct way to give change by using two smaller denominations, the above algorithm is not optimal.
EX: Need 5 change. Change bills are 2s, 3s, and 4s. The above algorithm would pick a 4 and be unable to make proper change when change can be gathered with a 2 and 3.



- **4b.**




- **4c.**


- **5a.**



- **5b.**




- **5c.**
