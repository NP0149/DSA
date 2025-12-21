# Boundary Traversal

[Problem Link](https://takeuforward.org/plus/dsa/problems/boundary-traversal)


```
class Solution {

    static boolean isLeaf(TreeNode root){
        return root.left == null && root.right == null;
    }

    static void preorder_of_leafs(TreeNode root, List<Integer> li){
        if(root == null) return;

        if(isLeaf(root)){
            li.add(root.data);
            return;
        }

        preorder_of_leafs(root.left, li);
        preorder_of_leafs(root.right, li);
    }

    static void find_all_left(TreeNode root, List<Integer> li){
        TreeNode curr = root;
        while(curr != null){
            if(!isLeaf(curr)){
                li.add(curr.data);
            }
            if(curr.left != null) curr = curr.left;
            else curr = curr.right;
        }
    }

    static void find_all_right(TreeNode root, List<Integer> li){
        Stack<Integer> st = new Stack<>();
        TreeNode curr = root;

        while(curr != null){
            if(!isLeaf(curr)){
                st.push(curr.data);
            }
            if(curr.right != null) curr = curr.right;
            else curr = curr.left;
        }

        while(!st.isEmpty()){
            li.add(st.pop());
        }
    }

    public List<Integer> boundary(TreeNode root) {
        List<Integer> li = new ArrayList<>();
        if(root == null) return li;

        if(!isLeaf(root)){
            li.add(root.data);
        }

        find_all_left(root.left, li);
        preorder_of_leafs(root, li);
        find_all_right(root.right, li);

        return li;
    }
}

```
# Complexity Analysis

Time:O(n)

Space:O(H)
