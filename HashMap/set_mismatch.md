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

Time:O(N)

Space:O(N)

# Approach-II


```

class Solution {
    public int[] findErrorNums(int[] arr) {
        Arrays.sort(arr);
         int n = arr.length;
        int nums[] = new int[n];
        int j = 0;
        int repeat[]=new int[2];
        if(n==2 || n==1){
            nums[0]=arr[0];
            repeat[0]=arr[0];
        }
        for (int i = 0; i < arr.length; i++) {
                    // Check if the current element is unique
                    if ((i == 0 || arr[i] != arr[i - 1]) && (i == arr.length - 1 || arr[i] != arr[i + 1])) {
                    nums[j]=arr[i];
                    j++;
                    }
                    else if((i==0 || arr[i]!=arr[i-1]) && (i==arr.length-1 || arr[i]==arr[i+1])){
                        nums[j]=arr[i];
                        repeat[0]=arr[i];
                        j++;
            }

            }
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=nums[i];
        }
        int miss=(n*(n+1)/2)-sum;
        repeat[1]=miss;
        return repeat;
        }


}
```

# Complexities

Time:O(nlogn)

Space:O(N):




