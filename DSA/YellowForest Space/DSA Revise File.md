# Two Sum [LeetCode - [[Problem](https://leetcode.com/problems/two-sum/description/)]]

## **Pattern**
- HashMap
- Remaining Value

## **Intuition**
- We know that any two sum contains (a + b = c) where b = c - a
- We are constantly checking if the array contains b, why using the current arr[i] as `a` and target as `c`
- If array contains `b` then the equation completes; else return `{-1, 1}`

## **Trick/Technique**
- Create a hashmap with (key, value) where key is `arr[i]` and value is its `index`
- Run the loop, keep checking remaining `b` as `arr[i]` 
- If found, then return its `index` and current `i` else return `{-1,-1}`


# Code

```java
for (int i = 0; i < arr.length; i++) {
            int remainingValue = target - arr[i];
            if (hashMap.containsKey(remainingValue)){
                return new int[] {i, hashMap.get(remainingValue)};
            }
            hashMap.put(arr[i], i);

        }
```
