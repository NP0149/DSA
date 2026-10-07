# Maximum path sum between two leaves

[Problem Link](https://www.geeksforgeeks.org/problems/maximum-path-sum/1)


```
/* Node Structure
class Node
{
    int data;
    Node left, right;

    Node(int item)
    {
        data = item;
        left = right = null;
    }
} */
class Solution {
    int maxsum=Integer.MIN_VALUE;
    int leafcount=0;
    int find(Node root){
        if(root==null){
            return 0;
        }
        if(root.left==null && root.right==null){
            leafcount++;
        return root.data;
        }
        int left=find(root.left);
        int right=find(root.right);
        if(root.left!=null && root.right!=null){
            maxsum=Math.max(maxsum,left+right+root.data);
        }
        if(root.left==null){
            return root.data+right;
        }
        if(root.right==null){
            return root.data+left;
        }
        return root.data+Math.max(left,right);
    }
    public int maxPathSum(Node root) {
     find(root);
     if(leafcount<2){
         return -1;
     }
     return maxsum;
    }
}
```
