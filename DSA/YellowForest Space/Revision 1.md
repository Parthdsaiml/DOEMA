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
