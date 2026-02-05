# Maximum number of ones with k zeroes replacement

[Problem Link](https://www.geeksforgeeks.org/problems/maximize-number-of-1s0905/1)

```
class Solution {
    public int maxOnes(int arr[], int k) {
        int count0=0;
        int count1=0;
        int maxcount=0;
        int l=0;
        for(int i=0;i<arr.length;i++){
            if(arr[i]==1){
                count1++;
            }
            else{
                count0++;
            }
            while(count0>k){
                if(arr[l]==0){
                    count0--;
                }
                else{
                    count1--;
                }
                l++;
            }
            maxcount=Math.max(maxcount,i-l+1);
        }
        return maxcount;
    }
}
```
# Complexity Anlaysis

Time:O(n)

Space;O(1)
