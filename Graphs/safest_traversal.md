[Problem Link](https://leetcode.com/problems/find-the-safest-path-in-a-grid/)


```
class Solution {

    int n;
    int[][] dist;
    int[][] dir = {{0,1}, {0,-1}, {1,0}, {-1,0}};

    public int maximumSafenessFactor(List<List<Integer>> grid) {

        n = grid.size();
        dist = new int[n][n];

        Queue<int[]> q = new LinkedList<>();

        // Step 1: Initialize all thief positions
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {

                if(grid.get(i).get(j) == 1) {
                    q.offer(new int[]{i,j});
                    dist[i][j] = 0;
                }
                else {
                    dist[i][j] = -1;
                }
            }
        }

        // Step 2: Multi-source BFS
        while(!q.isEmpty()) {

            int[] curr = q.poll();

            int r = curr[0];
            int c = curr[1];

            for(int[] d : dir) {

                int nr = r + d[0];
                int nc = c + d[1];

                if(nr >= 0 && nr < n &&
                   nc >= 0 && nc < n &&
                   dist[nr][nc] == -1) {

                    dist[nr][nc] = dist[r][c] + 1;

                    q.offer(new int[]{nr,nc});
                }
            }
        }

        // Step 3: Binary Search
        int low = 0;
        int high = 2 * n;
        int ans = 0;

        while(low <= high) {

            int mid = low + (high - low) / 2;

            if(isPossible(mid)) {

                ans = mid;
                low = mid + 1;

            }
            else {

                high = mid - 1;
            }
        }

        return ans;
    }

    // Check whether a path exists with safeness >= k
    boolean isPossible(int k) {

        if(dist[0][0] < k)
            return false;

        boolean[][] vis = new boolean[n][n];

        Queue<int[]> q = new LinkedList<>();

        q.offer(new int[]{0,0});
        vis[0][0] = true;

        while(!q.isEmpty()) {

            int[] curr = q.poll();

            int r = curr[0];
            int c = curr[1];

            if(r == n-1 && c == n-1)
                return true;

            for(int[] d : dir) {

                int nr = r + d[0];
                int nc = c + d[1];

                if(nr >= 0 && nr < n &&
                   nc >= 0 && nc < n &&
                   !vis[nr][nc] &&
                   dist[nr][nc] >= k) {

                    vis[nr][nc] = true;
                    q.offer(new int[]{nr,nc});
                }
            }
        }

        return false;
    }
}
```
