# maximum sub array sum

# Approach-I

consider all the combinations of the subarrays,so we need to use loop in loop to achieve it,so the time complexity becomes order of n^2
but space complexity will be O(1)

```Java
class main{
 public static void main(String args[]){
   int arr[]={-3,5,4,7,-1,-2};
   int n=arr.length;
   int maxsubarrsum=0;
   int stindex=0;
   int endindex=0;
   for(int i=0;i<n;i++){
   int subarrsum=0;
 for(int j=i;j<n;j++){
  subarrsum+=arr[j];
  if(subarrsum>maxsubarrsum){
maxsubarrsum=subarrsum;
stindex=i;
endindex=j;
  }
  }
  }
```

# Approach-II(kadanes algorithm)

+ve + +ve=+ve

+ve + (small)-ve=+ve

+ve + (big)-ve=-ve

if sum becomes negative then reset the sum to zero and compare with the maximum sub array sum

```Java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxsubarrsum=-1000000000;
        int subarrsum=0;
        for(int i=0;i<nums.length;i++){
            subarrsum=subarrsum+nums[i];
            maxsubarrsum=Math.max(subarrsum,maxsubarrsum);
            if(subarrsum<0)
            subarrsum=0;
        }
        return maxsubarrsum;
    }
    }
```

# complexities

Time complexity:O(n);

space complexity:O(1);


