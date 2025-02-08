# ROTATING ARRAY K TIMES
[Problem link](https://leetcode.com/problems/rotate-array

Approch:
1)we need to reverse the total array first
2)reverse the array from 0 to k-1;
3)reverse the array from k to n-1;
so the array will be rotated K times
```Java
class Solution {
    static void rev(int arr[],int i,int j){
        int n=arr.length;
        while(i<j){
            int temp=arr[i];
            arr[i]=arr[j];
            arr[j]=temp;
            i++;
            j--;
        }
    }
    public int[] rotate(int[] nums, int k) {
        int n=nums.length;
        k=k%n;
        if(n==0 || n==1){
            return nums;
        }
        rev(nums,0,n-1);
        rev(nums,0,k-1);
        rev(nums,k,n-1);
        return nums;
    }
}
```
time complexity:O(N);
