# set mismatch

[Problem Link](https://leetcode.com/problems/set-mismatch/)

# Approach-I

1)add the elements into hash set if they are repeating then donot add in the hash set, when the element is repeating then 
 in else you need add it to the arr,and then by using formula n*(n-1)/2,we can find the missing element in the array

 ```
class Solution {
    public int[] findErrorNums(int[] nums) {
        int n=nums.length;
       HashSet<Integer> hs=new HashSet<>();
       int arr[]=new int[2];
       for(int i=0;i<n;i++){
        if(!hs.contains(nums[i])){
            hs.add(nums[i]);
        }
        else{
            arr[0]=nums[i];
        }
       }
       int sum=0;
       for(int num:hs){
        sum+=num;
       }
       int mis=n*(n+1)/2-sum;
       arr[1]=mis;
    return arr;
}
}

```

# Complexities

Time:O
