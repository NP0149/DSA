# Maximal rectangle

[Problem Link](https://leetcode.com/problems/maximal-rectangle/)

```
class Solution {
     static int[] find_pse(int arr[]){
        int nse[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        int n=arr.length;
        for(int i=0;i<n;i++){
            while(!st.isEmpty() && arr[st.peek()]>arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                nse[i]=-1;
            }
            else{
                nse[i]=st.peek();
            }
            st.push(i);
        }
        return nse;
    }
    static int[] find_nse(int arr[]){
        int nse[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        int n=arr.length;
        for(int i=n-1;i>=0;i--){
            while(!st.isEmpty() && arr[st.peek()]>=arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                nse[i]=n;
            }
            else{
                nse[i]=st.peek();
            }
            st.push(i);
        }
        return nse;
    }
    static int find_max(int arr[]){
        Stack<Integer> st=new Stack<>();
        int nse[]=find_nse(arr);
        int pse[]=find_pse(arr);
        int area=0;
        int maxarea=Integer.MIN_VALUE;
        for(int i=0;i<arr.length;i++){
            int k=nse[i]-pse[i]-1;
          area=arr[i]*k;
          maxarea=Math.max(maxarea,area);
        }
        return maxarea;
    }
    public int maximalRectangle(char[][] matrix) {
        int n=matrix.length;
        int m=matrix[0].length;
        int mat[][]=new int[n][m];
        for(int i=0;i<m;i++){
            int k=0;
            for(int j=0;j<n;j++){
                if(matrix[j][i]=='1'){
                   mat[j][i]=k+1;
                   k++;
                }
                else{
                    mat[j][i]=0;
                    k=0;
                }
            }
        }
            int maxarea=Integer.MIN_VALUE;
            for(int arr[]:mat){
               maxarea=Math.max(maxarea,find_max(arr));
            }
            return maxarea;
        }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n X M) --> because of the extra matrix

