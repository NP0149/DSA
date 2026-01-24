# Maximum people visible in a line

[Problem Link](https://www.geeksforgeeks.org/problems/maximum-people-visible-in-a-line/1)

```
class Solution {
    public int maxPeople(int[] arr) {
   int n = arr.length;
        if (n == 0) return 0;

        int[] leftCount = new int[n];
        int[] rightCount = new int[n];
        Stack<Integer> stack = new Stack<>();

        // Calculate visibility to the left
        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && arr[stack.peek()] < arr[i]) {
                stack.pop();
            }
            // If stack is empty, they see everyone to the left: index i
            // If not, they see everyone between them and the 'wall': i - stack.peek() - 1
            leftCount[i] = stack.isEmpty() ? i : (i - stack.peek() - 1);
            stack.push(i);
        }

        stack.clear();

        // Calculate visibility to the right
        for (int i = n - 1; i >= 0; i--) {
            while (!stack.isEmpty() && arr[stack.peek()] < arr[i]) {
                stack.pop();
            }
            // If stack is empty, they see everyone to the right: (n - 1) - i
            // If not, they see: stack.peek() - i - 1
            rightCount[i] = stack.isEmpty() ? (n - 1 - i) : (stack.peek() - i - 1);
            stack.push(i);
        }

        int maxSeen = 0;
        for (int i = 0; i < n; i++) {
            maxSeen = Math.max(maxSeen, leftCount[i] + rightCount[i] + 1);
        }

        return maxSeen;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
