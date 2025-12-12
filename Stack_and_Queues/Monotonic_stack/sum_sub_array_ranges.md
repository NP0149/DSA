# Sum of sub array ranges

[Problem Link](https://leetcode.com/problems/sum-of-subarray-ranges/)

```
class Solution {
    static int[] findpse(int arr[]){
        int pse[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        int n=arr.length;
        for(int i=0;i<n;i++){
            while(!st.isEmpty() && arr[st.peek()]>arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                pse[i]=-1;
            }
            else{
                pse[i]=st.peek();
            }
            st.push(i);
        }
        return pse;
    }
    static int[] findnse(int arr[]){
        int nse[]=new int[arr.length];
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
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
    static long find_totalsmall(int arr[]){
        int n=arr.length;
        int mod=(int)(1e9+7);
        int pse[]=findpse(arr);
        int nse[]=findnse(arr);
        long total=0;
        for(int i=0;i<n;i++){
            long left=i-pse[i];
            long right=nse[i]-i;
         long contr=left*right*1L;
         total+=(contr*arr[i]);
        }
        return total;
    }
    static int[] findnge(int arr[]){
       int nge[]=new int[arr.length];
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        for(int i=n-1;i>=0;i--){
         while(!st.isEmpty() && arr[st.peek()]<=arr[i]){
            st.pop();
         }
         if(st.isEmpty()){
            nge[i]=n;
         }
         else{
            nge[i]=st.peek();
         }
         st.push(i);
        }
        return nge;
    }
    static int[] findpge(int arr[]){
       int pge[]=new int[arr.length];
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<arr.length;i++){
         while(!st.isEmpty() && arr[st.peek()]<arr[i]){
            st.pop();
         }
         if(st.isEmpty()){
            pge[i]=-1;
         }
         else{
            pge[i]=st.peek();
         }
         st.push(i);
        }
        return pge;
    }
    static long find_totallarge(int arr[]){
        int n=arr.length;
        int mod=(int)(1e9+7);
        int nge[]=findnge(arr);
        int pge[]=findpge(arr);
        long total=0;
        for(int i=0;i<n;i++){
            long left=i-pge[i];
            long right=nge[i]-i;
 long contr=left*right*1L;
         total+=(contr*arr[i]);
        }
        return total;
    }
    public long subArrayRanges(int[] arr) {
      long totalsmall=find_totalsmall(arr);
      long totallarge=find_totallarge(arr);
      return totallarge-totalsmall;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
