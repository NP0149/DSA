# Missing number in array
[Problem link](https://www.geeksforgeeks.org/problems/missing-number-in-array1416/1)

# Approch I

We need to consider the n value as array length+1 sowe will get the n value by substituting n value in the natural numbers sum formula that is 
n*(n+1)/2 then will get actual sum of the n+1 natural numbers 
so we need to consider the sum of array elements and then missing comes out to be the difference between natural sum and array ele sum

```Java
class Solution {
    long missingNumber(int arr[]) {
       long n=arr.length+1;
 long sum=n*(n+1)/2;
 long sum1=0;
 for(int i=0;i<arr.length;i++){
  sum1=sum1+arr[i];
  }
  long missing=Math.abs(sum-sum1);
  return missing;
    }
}
```

# Complexities

time complexity:O(N);
space complexity:O(1);
