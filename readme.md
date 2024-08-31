
# Time Complexity Analysis of For Loop with Set Operations

## Overview

In this document, we'll analyze the time complexity of a Python function that performs operations on a set. The common misconception is that nested loops or loops with checks inside always lead to $$ O(n^2) $$time complexity. However, this is not always the case, especially when using efficient data structures like sets.

## Function Definition

Here's the function we'll be analyzing:

```python
      def checkIfExist(self, arr: List[int]) -> bool:
          seen = set()
          for n in arr:
              if 2 * n in seen or (n % 2 == 0 and n // 2 in seen):
                  return True
              else:
                  seen.add(n)
          return False
```
## Key Points

### Set Operations

The efficiency of the algorithm depends heavily on the data structure used. In this case, we use a set, which provides average $$O(1)$$ time complexity for membership checks and insertions due to its hash table implementation.

**Breakdown:**

-   **For Loop:** Iterates through each element in the array, resulting in $$O(n)$$ time complexity.
-   **Set Operations:**
    -   **Membership Checks:** `x in seen` and `n // 2 in seen` both have $$O(1)$$ average time complexity.
    -   **Insertion:** `seen.add(n)` also has $$O(1)$$ average time complexity.

### Combined Time Complexity

Since the loop runs $$ O(n) $$ times and each iteration involves $$ O(1) $$operations, the total time complexity is $$ O(n)×O(1)=O(n^2) $$.

## Important Distinction

-   **List vs. Set:** If `seen` were a list instead of a set, membership checks would be $$ O(n^2) $$, leading to an overall time complexity of $$ O(n^2) $$.
-   **Set Efficiency:** The use of a set ensures that membership checks remain efficient, resulting in O(n)O(n)O(n) time complexity.

## Conclusion

The time complexity of the function is $$O(n)$$, not $$
O(n^2)
$$, because the `in` operation on a set is $$ O(1) $$ on average.


The `in` operation inside a `for` loop will result in an $$ O(n^2) $$ time complexity if the `in` operation has a time complexity of $$O(n)$$ and the loop runs n times. This scenario typically occurs when the `in` operation is applied to a data structure that requires linear search, such as a list or a linked list.

### Cases Where `in` Inside a `for` Loop Becomes $$O(n^2)$$:

1.  **Using a List or Linked List**:
    
    -   **List**: If you check for membership (`x in list`) inside a `for` loop, Python will perform a linear search, which takes $$O(n)$$ time for each check. If the loop runs nnn times, the overall time complexity becomes O(n)×O(n)=$$ O(n^2) $$
    -   **Linked List**: Similarly, in a linked list, the `in` operation would also take $$O(n)$$ time because each element has to be traversed to check for membership.
    
    ### Example:
    
    ```python
    
    arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    result = []
    
    for i in arr:
        if i in result:
            continue
        result.append(i)
    -   
**Time Complexity**: Here, `if i in result` is an $$O(n) $$operation when `result` is a list. Since this check happens inside a loop that runs nnn times, the overall time complexity becomes $$O(n^2)$$.
2.  **Using Strings**:
    
    -   **String Search**: Checking if a substring exists within a string (`sub in string`) requires a linear search if the substring is not found at the beginning. If this operation is done inside a loop iterating over the string or substrings, it could lead to $$ O(n^2) $$ complexity.
    
    ### Example:
    
    ```python
    string = "abcdefg"
    substrings = []
    
    for c in string:
        if c in substrings:
            continue
        substrings.append(c)` 
    ```
    -   **Time Complexity**: Here, checking `c in substrings` is $$ O(n) $$ because `substrings` is a list of characters. If the loop runs for each character in the string, the time complexity becomes $$ O(n^2) $$.
3.  **Nested List Searching**:
    
    -   If you have nested lists and you're checking for membership in a nested list using `in` within a loop that iterates over another list, you could end up with $$ O(n^2) $$ time complexity.
    
    ### Example:
    
    ```python
    
    list_of_lists = [[1, 2], [3, 4], [5, 6], [7, 8], [9, 10]]
    
    for sublist in list_of_lists:
        if 1 in sublist:
            break` 
    ```
    -   **Time Complexity**: Here, checking `1 in sublist` is $$O(m)$$ where mmm is the average length of the sublists. If each sublist has an average length proportional to nnn and there are nnn sublists, the overall time complexity can approach $$ O(n^2) $$.

### Summary:

-   The `in` operation inside a `for` loop becomes $$ O(n^2) $$ when the `in` operation itself is $$O(n)$$, which happens when using data structures like lists, linked lists, or strings.
-   This situation typically arises when you're performing a linear search within each iteration of a loop that runs nnn times.

In contrast, using `in` with data structures like sets or dictionaries (where membership checks are $$O(n)$$on average) inside a loop will maintain an overall $$ O(n) $$ time complexity.


