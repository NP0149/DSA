# check if array is sorted and rotated

[Problem Link](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/)

# Approach-I

1)check if array is sorted in normal manner

2)if array is rotated consider the position and then rotate the array by k positions if the rotated array is in sorted manner then we can say that array is sorted and rotated

```
class Solution {
    public static void rev(int arr[],int low,int high){
        int i=low;
        int j=high;
        while(i<j){
            int temp=arr[i];
            arr[i]=arr[j];
            arr[j]=temp;
            i++;
            j--;
        }
    }
    public static void rotate(int arr[],int k){
        int n=arr.length;
        k=k%n;
        rev(arr,0,n-1);
        rev(arr,0,k-1);
        rev(arr,k,n-1);
    }
    public boolean check(int[] arr) {
        int n=arr.length;
        int i=0;
        int count=0;
        int k=0;
        while(i<n-1){
            if(arr[i]>arr[i+1]){
                count++;
                k=i+1;
            }
            i++;
        }
        int l=0;
        if(count==1){
           k=n-k;
          rotate(arr,k);
           int j=0;
           while(j<n-1){
            if(arr[j]>arr[j+1]){
                return false;
            }
            j++;
           }
            return true;
        }
        else if(count==0){
            return true;
        }
        else{
            return false;
        }

    }
}
```
# Complexities

Time:O(n);//n is the length of the array

Space:O(1);
