[Problem Link](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/submissions/2193111124/)

```
class Solution {
    TreeNode find(int arr[],int low,int high){
        if(low>high){
            return null;
        }
        int mid=low+(high-low)/2;
        TreeNode root=new TreeNode(arr[mid]);
        root.left=find(arr,low,mid-1);
        root.right=find(arr,mid+1,high);
        return root;
    }
    public TreeNode sortedArrayToBST(int[] arr) {
        return find(arr,0,arr.length-1);
    }
}
```
