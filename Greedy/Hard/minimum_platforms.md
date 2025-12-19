# Minimum number of platforms

[Problem Link](https://www.geeksforgeeks.org/problems/minimum-platforms-1587115620/1)


```
class Solution {
    public int minPlatform(int arr[], int dep[]) {
        //  code here
        int i=0;
        int j=0;
        Arrays.sort(arr);
        Arrays.sort(dep);
        int maxcount=0;
        int count=0;
        while(i<arr.length){
            if(arr[i]<=dep[j]){
                count++;
                i++;
            }
            else{
                count--;
                j++;
            }
            maxcount=Math.max(count,maxcount);
        }
        return maxcount;
    }
}
```

# Complexity Analysis

Time:O(2n)

Space:O(1)
