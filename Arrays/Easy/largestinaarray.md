largest element in a array
[problem link][https://www.geeksforgeeks.org/problems/largest-element-in-array4009/0]
class Solution {
    public static int largest(int[] arr) {
        int n=arr.length;
        int max=arr[0];
        for(int i=0;i<n;i++){
           if(max<arr[i]){
               max=arr[i];
           }
        }
       return max; // code here
    }
}
