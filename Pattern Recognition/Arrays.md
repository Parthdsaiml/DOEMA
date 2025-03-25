# Patterns instead of Question to remember 

### **1️⃣ Prefix Sum (Cumulative Sum)**  
**When to use**:  
- Problems involving **subarray sums**, equilibrium indices, or range queries.  

**Examples**:  
- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)  
- [Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)  
- [Range Sum Query 2D](https://leetcode.com/problems/range-sum-query-2d-immutable/)  

**Key Trick**:  
- Precompute `prefix_sum[i] = sum(arr[0..i])` → Convert subarray sum `sum(arr[i..j])` to `prefix_sum[j] - prefix_sum[i-1]`.  
- Use a **hashmap** to track frequency of prefix sums (e.g., count subarrays with sum `K`).  

---

### **2️⃣ Two Pointers**  
**When to use**:  
- **Sorted arrays**, in-place modifications, or merging.  

**Examples**:  
- [Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) (sorted array)  
- [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)  
- [Merge Sorted Arrays](https://leetcode.com/problems/merge-sorted-array/)  

**Key Trick**:  
- Use `left` (start) and `right` (end) pointers. Adjust based on conditions:  
  - `sum < target` → `left++`  
  - `sum > target` → `right--`  

---

### **3️⃣ Sliding Window (Fixed/Variable Size)**  
**When to use**:  
- **Contiguous subarrays/substrings** with constraints (e.g., max/min length, sum, or uniqueness).  

**Examples**:  
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) (Kadane’s)  
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)  
- [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)  

**Key Trick**:  
- Expand `right` until a condition breaks → shrink `left` to restore validity.  
- Track window state with a **hashmap** (frequency) or **counter**.  

---

### **4️⃣ Monotonic Stack**  
**When to use**:  
- Finding **next/previous greater/smaller elements** or **histogram** problems.  

**Examples**:  
- [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)  
- [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)  
- [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)  

**Key Trick**:  
- Maintain a stack with **strictly increasing/decreasing** elements.  
- For "next greater element," process elements in reverse.  

---

### **5️⃣ Kadane’s Algorithm (Maximum Subarray)**  
**When to use**:  
- Maximizing/minimizing **contiguous subarray sums** (even with negatives).  

**Examples**:  
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)  
- [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)  
- [Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)  

**Key Trick**:  
- Track `current_max = max(arr[i], current_max + arr[i])` → reset if `current_max` becomes negative.  

---

### **6️⃣ Binary Search on Answer**  
**When to use**:  
- Minimizing/maximizing values under constraints (e.g., "smallest subarray with sum ≥ X").  

**Examples**:  
- [Find Kth Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/)  
- [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)  
- [Minimum Limit of Balls in a Bag](https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/)  

**Key Trick**:  
- Define `low` and `high` bounds → check feasibility of `mid` using a helper function.  

---

### **7️⃣ Hash Map / Frequency Counter**  
**When to use**:  
- Tracking **element frequencies**, subarrays with sum `K`, or duplicates.  

**Examples**:  
- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)  
- [Two Sum](https://leetcode.com/problems/two-sum/)  
- [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)  

**Key Trick**:  
- Use `defaultdict(int)` or `Counter` to store counts.  
- For subarrays with sum `K`, track `prefix_sum` frequencies.  

---

### **8️⃣ Cyclic Sort**  
**When to use**:  
- Arrays with elements in a **fixed range** `[1, n]` (e.g., finding missing/duplicate numbers).  

**Examples**:  
- [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)  
- [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)  
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)  

**Key Trick**:  
- Place each element at its correct index `arr[i] = i+1` by swapping.  

---

### **9️⃣ Dutch National Flag (3-Way Partitioning)**  
**When to use**:  
- Partitioning arrays into **2/3 regions** (e.g., sorting 0s, 1s, and 2s).  

**Examples**:  
- [Sort Colors](https://leetcode.com/problems/sort-colors/)  
- [Separate Odd and Even Numbers](https://www.geeksforgeeks.org/segregate-even-odd-numbers-set-3/)  
- [Move Zeroes](https://leetcode.com/problems/move-zeroes/) (2-way partition)  

**Key Trick**:  
- Use `low`, `mid`, `high` pointers → swap elements to their correct regions.  

---

### **🔟 In-place Reversals**  
**When to use**:  
- Rotating arrays, reversing subarrays, or cyclic shifts.  

**Examples**:  
- [Rotate Array](https://leetcode.com/problems/rotate-array/)  
- [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)  
- [Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)  

**Key Trick**:  
- Reverse the entire array → reverse subarrays.  
- For rotations: `reverse(arr[0..n-k-1]) → reverse(arr[n-k..n-1]) → reverse entire array`.  

---

### **1️⃣1️⃣ Matrix Traversal (2D Arrays)**  
**When to use**:  
- Spiral/diagonal traversal, searching in sorted matrices.  

**Examples**:  
- [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)  
- [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)  
- [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)  

**Key Tricks**:  
- Use **layer-by-layer** traversal for spirals.  
- For sorted matrices: start from the **top-right corner** and move left/down.  

---

### **1️⃣2️⃣ Bit Manipulation**  
**When to use**:  
- Problems involving **bitwise operations** (XOR, AND, OR).  

**Examples**:  
- [Single Number](https://leetcode.com/problems/single-number/)  
- [Subsets](https://leetcode.com/problems/subsets/) (using bitmasking)  
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)  

**Key Trick**:  
- XOR all elements to find duplicates/missing numbers.  
- Use bitmasking to generate subsets.  

---

### **1️⃣3️⃣ Dynamic Programming (1D/2D)**  
**When to use**:  
- Problems with **overlapping subproblems** (e.g., longest increasing subsequence).  

**Examples**:  
- [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)  
- [Coin Change](https://leetcode.com/problems/coin-change/)  
- [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)  

**Key Trick**:  
- Define `dp[i]` as the optimal solution up to index `i`.  
- For LIS: `dp[i] = max(dp[j] + 1 for j < i if arr[j] < arr[i])`.  

---

### **1️⃣4️⃣ Flood Fill (DFS/BFS)**  
**When to use**:  
- Traversing connected regions (islands, rotting oranges).  

**Examples**:  
- [Number of Islands](https://leetcode.com/problems/number-of-islands/)  
- [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)  
- [Flood Fill](https://leetcode.com/problems/flood-fill/)  

**Key Trick**:  
- Mark visited cells to avoid cycles.  
- Use BFS for shortest path in unweighted grids.  

---

### **1️⃣5️⃣ Reservoir Sampling**  
**When to use**:  
- Randomly selecting `k` elements from a stream (unknown size).  

**Examples**:  
- [Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)  
- [Random Pick Index](https://leetcode.com/problems/random-pick-index/)  

**Key Trick**:  
- For the `i-th` element, select it with probability `k/i`.  

---

### **1️⃣6️⃣ Mo’s Algorithm**  
**When to use**:  
- Answering **range queries** efficiently (offline processing).  

**Examples**:  
- [Range Sum Query](https://leetcode.com/problems/range-sum-query-immutable/)  
- [Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)  

**Key Trick**:  
- Sort queries and process them in **√n blocks** for O(√n) per query.  

---

### **1️⃣7️⃣ Segment Trees / Fenwick Trees**  
**When to use**:  
- Range queries (sum, min, max) with frequent updates.  

**Examples**:  
- [Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/)  
- [Count of Range Sum](https://leetcode.com/problems/count-of-range-sum/)  

**Key Trick**:  
- Segment Trees for O(log n) updates/queries.  
- Fenwick Trees (BIT) for prefix sums.  

---

### **1️⃣8️⃣ Greedy Algorithms**  
**When to use**:  
- Problems where **locally optimal choices** lead to a global optimum.  

**Examples**:  
- [Jump Game](https://leetcode.com/problems/jump-game/)  
- [Gas Station](https://leetcode.com/problems/gas-station/)  
- [Maximum Swap](https://leetcode.com/problems/maximum-swap/)  

**Key Trick**:  
- For Jump Game: Track `max_reachable` index.  

---

### **1️⃣9️⃣ Backtracking**  
**When to use**:  
- Generating permutations, subsets, or combinations.  

**Examples**:  
- [Subsets](https://leetcode.com/problems/subsets/)  
- [Permutations](https://leetcode.com/problems/permutations/)  
- [Combination Sum](https://leetcode.com/problems/combination-sum/)  

**Key Trick**:  
- Use recursion + backtracking to explore all possibilities.  

---

### **2️⃣0️⃣ Topological Sort**  
**When to use**:  
- Dependency resolution (e.g., course scheduling).  

**Examples**:  
- [Course Schedule](https://leetcode.com/problems/course-schedule/)  
- [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)  

**Key Trick**:  
- Use Kahn’s algorithm (BFS + in-degree tracking).  

---

### **2️⃣1️⃣ Intervals**  
**When to use**:  
- Merging, inserting, or scheduling intervals.  

**Examples**:  
- [Merge Intervals](https://leetcode.com/problems/merge-intervals/)  
- [Insert Interval](https://leetcode.com/problems/insert-interval/)  
- [Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)  

**Key Trick**:  
- Sort intervals by start time → process greedily.  

---

### **2️⃣2️⃣ Quickselect**  
**When to use**:  
- Finding the **k-th smallest/largest element** without full sorting.  

**Examples**:  
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)  
- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)  

**Key Trick**:  
- Partition the array using a pivot (like Quicksort).  

---

### **2️⃣3️⃣ Boyer-Moore Voting Algorithm**  
**When to use**:  
- Finding **majority elements** (appearing > n/2 times).  

**Examples**:  
- [Majority Element](https://leetcode.com/problems/majority-element/)  
- [Majority Element II](https://leetcode.com/problems/majority-element-ii/)  

**Key Trick**:  
- Track a candidate and counter → increment/decrement based on matches.  

---

### **2️⃣4️⃣ Difference Array**  
**When to use**:  
- Range updates (e.g., add `k` to all elements from `i` to `j`).  

**Examples**:  
- [Range Addition](https://leetcode.com/problems/range-addition/)  
- [Corporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/)  

**Key Trick**:  
- Track `diff[i] = arr[i] - arr[i-1]` → apply updates in O(1).  

---

### **2️⃣5️⃣ Floyd’s Cycle Detection**  
**When to use**:  
- Detecting cycles in arrays (e.g., duplicates leading to infinite loops).  

**Examples**:  
- [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)  
- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)  

**Key Trick**:  
- Use **slow** and **fast** pointers → detect meeting point.  

---

### **🚀 Final Tips**  
1. **Recognize Patterns First**: Ask, *"Does this problem fit a known template?"*  
2. **Practice Variations**: Solve 2-3 problems per pattern to internalize the trick.  
3. **Combine Patterns**: Complex problems often mix multiple patterns (e.g., **Prefix Sum + Hashmap**).  

