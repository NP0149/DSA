# Minimum number of days to make m boquets with k flowers which are adjacent to each other

[Problem Link](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/submissions/1682128632/)

# Approach-I

1)low always points to minimum of array and high is max of array

2)write a function that considers mid as a day and then count=0 and total=0 ,if unbloomed flower came just count/k(number of flowers
flowers needed to make boquet)

3)if the total>number of boquets then return the smallest day,so move high to mid-1 else low=mid+1

```
class Solution {
    public static int fun(int arr[],int mid,int m,int k){
        int count=0;
        int total=0;
        for(int i=0;i<arr.length;i++){
            if(mid-arr[i]>=0){
                count++;
            }
            else{
            total+=count/k;
            count=0;
            }
        }
         total+=count/k;
         return total;
    }
    public int minDays(int[] arr, int m, int k) {
        int low=Integer.MAX_VALUE;
        int high=Integer.MIN_VALUE;
        int n=arr.length;
        for(int i=0;i<n;i++){
            high=Math.max(high,arr[i]);
            low=Math.min(low,arr[i]);
        }
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            //mid is the day
            int find=fun(arr,mid,m,k);
            if(find>=m){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return ans;
    }
}
```
# Complexities

Time:O(log(maxi-mini)*N);

Space:O(1)
