
```markdown
# 🚀 [Problem Name] - [LeetCode/Platform Link]  
*(Example: "209. Minimum Size Subarray Sum" → Link)*  

## 🧩 **Pattern**  
*(Sliding Window, BFS, DP, etc.)*  

## 💡 **Intuition**  
- 2-3 bullet points explaining **WHY** this pattern fits:  
  - *"Because the problem asks for X, and constraints Y suggest we need Z..."*  
  - *"Similar to Problem ABC but with a twist in..."*  

## 🔑 **Trick/Technique**  
- **Core Insight**: 1-line summary (e.g., "Expand right until condition fails, then shrink left")  
- **Edge Cases**: Key edge cases to handle (e.g., empty input, all duplicates)  
- **Code Snippet** (Python/Java):  
  ```python
  # Minimal code showing the TRICK (not full solution)
  left = 0
  for right in range(len(nums)):
      while window_condition:
          left += 1
  ```  

## ⏱️ **Time/Space Complexity**  
- **Time**: O(n) → Why? "Single pass with two pointers"  
- **Space**: O(1) → Why? "No extra data structures"  

## 🔄 **Variations**  
- Similar problems that use the **SAME** pattern:  
  1. [Problem Name + Link] *(e.g., "3. Longest Substring Without Repeating Characters")*  
  2. [Problem Name + Link] *(e.g., "904. Fruit Into Baskets")*  

## 📌 **Key Takeaways**  
1. "Use sliding window when the problem asks for **contiguous subarrays/substrings** with a condition."  
2. "Always track the window state with a hashmap or counter."  
```

---

### **Example Filled Template** (for revision):  

```markdown
# 🚀 [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)  

## 🧩 **Pattern**  
Sliding Window (Variable Size)  

## 💡 **Intuition**  
- Problem asks for **longest substring** → hints at sliding window.  
- Need to track **unique characters** → use a set/hashmap.  
- When a duplicate is found, move the left pointer until uniqueness is restored.  

## 🔑 **Trick/Technique**  
- **Core Insight**: Move `left` pointer to `max(left, last_seen[char] + 1)` when duplicates appear.  
- **Edge Cases**: Empty string, all unique characters.  
- **Code Snippet**:  
  ```python
  left = max_len = 0
  char_index = {}
  for right, char in enumerate(s):
      if char in char_index:
          left = max(left, char_index[char] + 1)
      char_index[char] = right
      max_len = max(max_len, right - left + 1)
  ```  

## ⏱️ **Time/Space Complexity**  
- **Time**: O(n) → Single pass with left/right pointers.  
- **Space**: O(min(n, 26)) → Store characters in a hashmap (for lowercase letters, O(26)).  

## 🔄 **Variations**  
1. [159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)  
2. [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)  

## 📌 **Key Takeaways**  
1. Sliding window + hashmap is ideal for **substring uniqueness** problems.  
2. Update `left` pointer **aggressively** to maintain the window's validity.  
```

---

### **Why This Template Works**  
1. **Pattern-First**: Forces you to categorize problems by **solution strategy**, not topic.  
2. **Minimalist Code**: Focuses on the CORE LOGIC, not boilerplate.  
3. **Connects Variations**: Links similar problems to build a "mental graph" of patterns.  
4. **Revision-Friendly**: Bold headers and bullet points let you skim notes in seconds.  

**Pro Tip**: Create a GitHub repo with folders like `Sliding Window`, `DFS`, `DP`, and store these templates there. Add a `README.md` with a pattern summary table! 🚀
