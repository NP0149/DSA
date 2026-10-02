
# Ceil value in bst

```
   int find_ceil(TreeNode root,int key){
        if(root==null){
            return -1;
        }
        int ceil=-1;
        while(root!=null){
            if(root.data==key){
                return key;
            }
            if(root.data>key){
                ceil=root.data;
                root=root.left;
            }
            else{
                root=root.right;
            }
        }
        return ceil;
     }
```
