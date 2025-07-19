# Replace part of the string

[Problem Link](https://leetcode.com/problems/remove-all-occurrences-of-a-substring/)

# Approach-I

```
class Solution {
    public String removeOccurrences(String s, String part) {
        while (s.contains(part)) {
            s = s.replaceFirst(part, "");
        }
        return s;
    }
}
```
# Complexities

Time:O(n)

Space:O(1)
