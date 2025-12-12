# Sub array minimums sum

[Problem Link](https://leetcode.com/problems/sum-of-subarray-minimums/)


```
class Solution {
    static int[] findpse(int arr[]){
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        int pse[]=new int[arr.length];
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
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        int nse[]=new int[arr.length];
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
    static int find(int arr[],int nse[],int pse[]){
    long total=0;
        int n=arr.length;
        int mod=(int)1e9+7;
        for(int i=0;i<n;i++){
           long left = i - pse[i];
        long right = nse[i] - i;

        long freq = (left * right) % mod;
        long contrib = (freq * arr[i]) % mod;

        total = (total + contrib) % mod; 
        }
        return (int)total;
    }
    public int sumSubarrayMins(int[] arr) {
    int nse[]=findnse(arr);
    int pse[]=findpse(arr);
    return find(arr,nse,pse);
    }
}

```

# Complexity Analysis

Time:O(n)

Space:O(n)
