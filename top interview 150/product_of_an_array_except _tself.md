# Product Of an array except itself

[Problem Link](https://leetcode.com/problems/product-of-array-except-self/)


# Approach-I(Brute force)

1) run two loops if i==j then skip that


   ```
    public class Solution{
    static int[] proprint(int arr[]){
        int n=arr.length;
        int c[]=new int[n];
        for(int i=0;i<n;i++){
            int pro=1;
            for(int j=0;j<n;j++){
                if(i!=j) {
                    pro *= arr[j];
                }
            }
            c[i]=pro;
        }
        return c;
    }

   ```
   # Complexities

   Time:O(N^2)

   Space:O(N)
   
# Approach-II

# They mentioned not to use division method ,but by using division method also we can solve the problem

```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int without=1;
        int pro=1;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            pro*=nums[i];
            hm.put(nums[i],hm.getOrDefault(nums[i],0)+1);
            if(nums[i]!=0){
                without*=nums[i];
            }
        }
        int ans[]=new int[nums.length];
        for(int i=0;i<nums.length;i++){
            if(nums[i]!=0){
                ans[i]=pro/nums[i];
            }
            else if(nums[i]==0){
                if(hm.get(0)>1){
                    ans[i]=0;
                }
                else{
                    ans[i]=without;
                }
            }
            else{

            }
        }
        return ans;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)

   # Approach -III

   1)find prefix product

   2)find the suffix product

   3)arr[i]=prefix[i]*suffix[i]


   ```
   class Solution {
    public int[] productExceptSelf(int[] arr) {
        int n=arr.length;
        int suffix[]=new int[n];
        int prefix[]=new int[n];
        suffix[n-1]=1;
        prefix[0]=1;
        for(int i=1;i<n;i++){
            prefix[i]=prefix[i-1]*arr[i-1];
        }
        for(int i=n-2;i>=0;i--){
            suffix[i]=suffix[i+1]*arr[i+1];
        }
        for(int i=0;i<n;i++){
            arr[i]=prefix[i]*suffix[i];
        }
        return arr;
    }
   }
   ```

   # Complexities

   Time:O(N)

   Space:O(1)


