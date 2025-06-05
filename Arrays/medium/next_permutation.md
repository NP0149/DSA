# Next Permutation

[Problem Link](https://leetcode.com/problems/next-permutation/submissions/1654330528/)

# Approach-I

1)we need to check from the last we need to check where the decreasing order breaks we need to consider that element as pivot.

2)we need to swap the pivot element with the next highest number..

3)and then we need to reverse the rest of the elements

```
public class next_permute {
    public static void swap(int arr[],int a,int b){
        int temp=arr[a];
        arr[a]=arr[b];
        arr[b]=temp;
    }
    public static void rev(int arr[],int low,int high){
        int i=low;
        int j=high;
        while(i<j){
            swap(arr,i,j);
            i++;
            j--;
        }
    }
    public static void permute(int[] arr) {
        int pivot=-1;
        int n=arr.length;
        for(int i=n-2;i>=0;i--){
            if(arr[i]<arr[i+1]){
                pivot=i;
                break;
            }
        }
        //if all the array is in decreasing order
        if(pivot==-1){
            rev(arr,0,n-1);
            return;
        }
        //need to swap the pivot element with the next large element
        int nextlarge=0;
        for(int i=n-1;i>pivot;i--){
            if(arr[i]>arr[pivot]){
                nextlarge=i;
                swap(arr,nextlarge,pivot);
                break;
            }
        }
        //reverse the rest array

        rev(arr,pivot+1,n-1);
         return;
    }
```

# Complexities

Time:O(n);

Space:O(1);
