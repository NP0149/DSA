# check children

[Problem Link](https://www.geeksforgeeks.org/problems/children-sum-parent/1)

```
class Solution {
    boolean checkChildrenSum(TreeNode root) { 
        // Your code goes here
        if(root==null) return true;
        if(root.left==null && root.right==null){
            return true;
        }
        if((root.left.val+root.right.val)!=root.val){
            return false;
        }
        return checkChildrenSum(root.left) && checkChildrenSum(root.right);
    }
}
```

# Complexity Anlaysis

Time:O(N)

Space:O(H)
