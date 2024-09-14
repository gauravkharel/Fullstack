Turns out, we optimize looking at the bigger picture. Such as memory of the system before optimizing our own applications. It turns out how big the system is and we duly use the ds and algo in a way to optimize our work in that particular system. 

The course comprises set of operations and, two different DS which are Arrays and Linked list and later about Dynamic Arrays. 

Python "list", js "Array object" is dynamic arrays


## Arrays in Typescript
### 1. **Basics of Array Operations**
   - **Accessing elements**: Access an element by its index in **O(1)** time, e.g., `arr[i]`.
   - **Inserting elements**:
     - At the end: **O(1)** time (unless the array resizes dynamically).
     - At the beginning/middle: **O(n)** time because elements must be shifted.
   - **Removing elements**:
     - From the end: **O(1)** time.
     - From the beginning/middle: **O(n)** time (due to shifting).
   - **Updating elements**: This is typically **O(1)** if you know the index.

### 2. **Understand Array Indexing**
   - **Zero-based indexing**: Arrays in TypeScript (and most languages) start from index 0.
   - Be careful with **off-by-one errors** when iterating, especially with loops.

### 3. **Array Traversal and Loops**
   - For common problems, you’ll often use loops to traverse arrays:
     - **For loop** (classic): Useful when you need control over the index.
       ```typescript
       for (let i = 0; i < arr.length; i++) {
           console.log(arr[i]);
       }
       ```
     - **For-of loop**: Simplifies iteration when you don’t care about the index.
       ```typescript
       for (let value of arr) {
           console.log(value);
       }
       ```
     - **While loop**: Used when the iteration condition is more complex.

### 4. **Edge Cases**:
   - **Empty arrays**: What happens if the array is empty? Handle this case to avoid errors.
   - **Single-element arrays**: Ensure your logic works even for arrays with one element.
   - **Arrays with duplicates**: Some problems require you to remove or handle duplicates.
   - **Sorted vs Unsorted arrays**: A sorted array can often lead to more optimized algorithms (like using binary search instead of linear search).

### 5. **Know Your Algorithms and Patterns**:
   - **Two Pointer Technique**:
     - Useful for problems like finding pairs, reversing arrays, or working with subarrays.
     - You maintain two pointers starting from different positions, often the start and end.
     ```typescript
     let left = 0;
     let right = arr.length - 1;
     while (left < right) {
         // Do something with arr[left] and arr[right]
         left++;
         right--;
     }
     ```
   - **Sliding Window**:
     - Commonly used for subarray-related problems (finding max sum subarrays, etc.).
     - It involves maintaining a "window" of elements and sliding it across the array while updating results.
     ```typescript
     let windowSum = 0;
     let k = 3;  // window size
     for (let i = 0; i < arr.length; i++) {
         windowSum += arr[i];
         if (i >= k - 1) {
             console.log(windowSum);
             windowSum -= arr[i - (k - 1)];
         }
     }
     ```

### 6. **Time and Space Complexity**:
   - **Time Complexity**: Understand how long an operation will take relative to the size of the array. For example:
     - **Accessing an element**: **O(1)**.
     - **Inserting/removing at the start or middle**: **O(n)** because shifting elements takes time.
     - **Searching for an element**: Typically **O(n)** unless the array is sorted (where you can use binary search to achieve **O(log n)**).
     
	 - **Space Complexity**: Consider how much extra memory your solution needs.
     - Modifying the array in-place (no extra space) vs. creating new arrays (uses more space).

### 7. **Common Array Problem Categories**:
   - **Searching**: Linear search, binary search (if sorted).
   - **Sorting**: Understanding how sorting algorithms (like quicksort, mergesort) work.
   - **Subarrays/Subsequences**: Finding subarrays with given properties (sum, product, etc.).
   - **Matrix (2D arrays)**: Handling multi-dimensional arrays with nested loops.

### 8. **Built-in Array Methods (TypeScript/JavaScript)**:
   - **push()**: Add an element to the end of the array.
   - **pop()**: Remove an element from the end.
   - **shift()**: Remove the first element.
   - **unshift()**: Add an element at the start.
   - **slice()**: Extract part of an array without modifying the original array.
   - **splice()**: Modify an array by adding/removing elements.
   - **map(), filter(), reduce()**: Functional programming methods for transforming arrays.

### 9. **Array Mutability**:
   - Arrays are **mutable**, meaning their contents can be changed even if the array is declared with `const`.
     ```typescript
     const arr = [1, 2, 3];
     arr[0] = 99;  // This is allowed
     ```
   - However, you cannot reassign the entire array if it's declared with `const`.

### 10. **Common Pitfalls**:
   - **Out-of-bounds access**: Accessing an index that doesn’t exist can cause errors or return `undefined`.
   - **Modifying an array while iterating**: Be cautious when adding or removing elements during iteration, as it may cause unexpected behavior.

---

### To Summarize:
When solving array problems, keep the following in mind:
1. **Basic operations**: Access, insert, delete.
2. **Edge cases**: Empty arrays, single elements, duplicates.
3. **Algorithms**: Two pointers, sliding window.
4. **Time/space complexity**: Aim for efficiency.
5. **Array methods**: Leverage built-in methods to simplify solutions.
6. **Test your solution** against different edge cases and large inputs to check for performance issues.

Problems I did for Arrays - Sep 10 2024: 
https://leetcode.com/problems/two-sum
https://leetcode.com/problems/valid-anagram/
