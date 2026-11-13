[Problem Link](https://leetcode.com/problems/smallest-string-with-a-given-numeric-value/)

```
class Solution {
    public String getSmallestString(int n, int k) {
        char arr[]=new char[n];
        for(int i=0;i<n;i++){
            arr[i]='a';
        }
        k=k-n;
      int i=arr.length-1;
       while(k>0 && i>=0){
        int val=Math.min(25,k);
        arr[i]=(char)('a'+val);
        k-=val;
        i--;
       }
       return new String(arr);
    }
}
```
