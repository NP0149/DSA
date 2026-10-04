# Number of formations with n nodes

```
class Solution {
    public int countTrees(int n) {

        int[] dp = new int[n + 1];

        dp[0] = 1;

        for (int nodes = 1; nodes <= n; nodes++) {

            for (int root = 0; root < nodes; root++) {

                int left = root;
                int right = nodes - 1 - root;

                dp[nodes] += dp[left] * dp[right];
            }
        }

        return dp[n];
    }
}
```
