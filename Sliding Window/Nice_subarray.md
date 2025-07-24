# Nice Subarray that the subarray that contains continuous k number of odd numbers

[Problem Link](https://leetcode.com/problems/count-number-of-nice-subarrays/description/)

# Approach-I

1)they asked us to find the subarray which is continuous and contains only k odd numbers.so we know the approach 

2)we need to find for the atmost k odd numbers and then subtract the atmost k-1 odd numbers

3)return that particular value

```
class Solution {
    public static int atmostk(int arr[],int k){
        int n=arr.length;
        int ans=0;
        int temp=0;
        int l=0;
        for(int i=0;i<n;i++){
            if(arr[i]%2==1){
                temp++;
            }
            while(temp>k){
                if(arr[l]%2==1){
                    temp--;
                }
                l++;
            }
            ans+=i-l+1;
        }
        return ans;
    }
    public int numberOfSubarrays(int[] arr, int k) {
        return atmostk(arr,k)-atmostk(arr,k-1);
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
