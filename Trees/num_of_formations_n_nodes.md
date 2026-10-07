# Number of formations with n nodes

```
class Solution {
    public int countTrees(int n) {

        int[] dp = new int[n + 1];

        dp[0] = 1;

        for (int i = 1; i <= n; i++) {

            for (int j = 0; j < i; i++) {

                int left = j;
                int right = i - 1 - j;

                dp[i] += dp[left] * dp[right];
            }
        }

        return dp[n];
    }
}
```
