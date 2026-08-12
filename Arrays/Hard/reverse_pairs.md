# reverse pairs

[Problem Link](https://leetcode.com/problems/reverse-pairs/submissions/2104201179/)


```
class Solution {
    static int count_pairs(int arr[],int l,int m,int r){
        int res=0;
        int j=m+1;
        for(int i=l;i<=m;i++){
        
           while(j<=r && (long)arr[i]>2L*arr[j]){
            j++;
           }
           res+=j-(m+1);
        }
        return res;
    }
    static void merge(int arr[],int l,int m,int r){
        int n1=m-l+1;
        int n2=r-m;
        int left[]=new int[n1];
        int right[]=new int[n2];
        for(int i=0;i<n1;i++){
            left[i]=arr[l+i];
        }
        for(int j=0;j<n2;j++){
            right[j]=arr[j+m+1];
        }
        int k=l;
        int i=0;
        int j=0;
        while(i<n1 && j<n2){
            if(left[i]<=right[j]){
                arr[k++]=left[i++];
            }
            else{
                arr[k++]=right[j++];
            }
        }
        while(i<n1){
            arr[k++]=left[i++];
        }
        while(j<n2){
            arr[k++]=right[j++];
        }
    }
    static int mergesort(int arr[],int l,int r){
        int res=0;
        if(l<r){
            int m=l+(r-l)/2;
            res+=mergesort(arr,l,m);
            res+=mergesort(arr,m+1,r);
            res+=count_pairs(arr,l,m,r);
            merge(arr,l,m,r);
        }
        return res;
    }
    public int reversePairs(int[] arr) {
        return mergesort(arr,0,arr.length-1);
    }
}
```
# Complexity 


Time:O(n logn)
