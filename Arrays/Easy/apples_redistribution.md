# Apple redistribution

[Problem Link](https://leetcode.com/problems/apple-redistribution-into-boxes/submissions/1886384366/)


```
class Solution {
    public int minimumBoxes(int[] apple, int[] arr) {
        int sum=0;
        for(int i=0;i<apple.length;i++){
            sum+=apple[i];
        }
        Arrays.sort(arr);
        int capacity=0;
        int count=0;
        for(int i=arr.length-1;i>=0;i--){
            if(sum>0){
                sum-=arr[i];
                count++;
                capacity+=arr[i];
            }
        }
        return count;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
