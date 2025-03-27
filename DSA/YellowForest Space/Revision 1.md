# Longest Common Prefix [Link]

## 🧩 **Pattern**  
*(Sorting, Two Pointer Approach)*
*(Just Two Pointer approach Brute Force)*

## 💡 **Intuition**  
- We Sort the array of strings and its sorted based on characters not length of words
- Now we take the first and last string and check their prefix
- Why this works
  - Because When we are checking the first and last string it automatically contains all the strings comed between
  - And to check the prefix we need to ensure that all strings does contain the same prefix so instead of checking one by one
  - We can Check just first and last one
  - And Sorting ensures that first and last string should based on their characters so similar prefix aligned togehter and non similar get shifted in other parts
  
## 🔑 **Trick/Technique**  
- **Core Insight**: Sort the array check the first and last word prefix all the similar prefix strings should sort together exist together
- **Edge Cases**: Make sure to cover the strings length 0 or 1 also
- **Code Snippet** (Python/Java):  
```java
class Solution {
    public String longestCommonPrefix(String[] strings) {
         Arrays.sort(strings);
        String firstString = strings[0];
        String lastString = strings[strings.length - 1];
        StringBuilder commonString = new StringBuilder();
        for (int i = 0; i < Math.min(firstString.length(), lastString.length()); i++) {
            if (firstString.charAt(i) != lastString.charAt(i)){
                return commonString.toString();
            }
            commonString.append(firstString.charAt(i));
            
        }
        return commonString.toString();
    }
}
```
## **Group Anagrams [Link]**  

### 🧩 **Pattern**  
*(Frequency Map, HashMap Approach)*  

### 💡 **Intuition**  
- Instead of sorting, we use a frequency map (array of size 26 for lowercase letters).  
- Each string's character count acts as a unique identifier (key) in a HashMap.  
- Anagrams will have the same frequency map, so they get grouped together.  

### 🔑 **Trick/Technique**  
- **Core Insight**: Convert each string into a character frequency array and use it as a key in a HashMap.  
- **Edge Cases**: Empty strings, all anagrams, no anagrams.  

### **Code Snippet** (Java)  
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> anagramMap = new HashMap<>();
        for (String str : strs) {
            int[] freq = new int[26];
            for (char c : str.toCharArray()) {
                freq[c - 'a']++;
            }
            String key = Arrays.toString(freq);
            
            anagramMap.putIfAbsent(key, new ArrayList<>());
            anagramMap.get(key).add(str);
        }
        return new ArrayList<>(anagramMap.values());
    }
}
```

---

## **Remove Element [Link]**  

### 🧩 **Pattern**  
*(Two Pointer Approach, In-Place Modification)*  

### 💡 **Intuition**  
- We use two pointers: one iterates over the array, the other keeps track of the valid position.  
- If an element matches the target, we skip it; otherwise, we move it to the valid position.  
- This avoids unnecessary shifts and maintains order for remaining elements.  

### 🔑 **Trick/Technique**  
- **Core Insight**: Use two pointers to overwrite unwanted elements and maintain a new valid length.  
- **Edge Cases**: Empty array, all elements match target, no elements match target.  

### **Code Snippet** (Java)  
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int validIndex = 0;
        for (int num : nums) {
            if (num != val) {
                nums[validIndex++] = num;
            }
        }
        return validIndex;
    }
}
```



