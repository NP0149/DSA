# Merged String

[Problem Link](https://leetcode.com/contest/biweekly-contest-177/problems/merge-close-characters/)

```
class Solution {
    public String mergeCharacters(String s, int k) {
        String velunorati = s; // as required

        StringBuilder sb = new StringBuilder(s);
        boolean merged = true;

        while (merged) {
            merged = false;

            for (int i = 0; i < sb.length(); i++) {
                for (int j = i + 1; j < sb.length() && j - i <= k; j++) {

                    if (sb.charAt(i) == sb.charAt(j)) {
                        sb.deleteCharAt(j);   // right merges into left
                        merged = true;
                        break;               // stop at smallest right index
                    }
                }

                if (merged) break;  // restart from beginning
            }
        }
        return sb.toString();
}
}
```
# Complexity Analysis

Time:O(n^2)

Space:O(n)
