# Count inversions

[Problem link](https://www.geeksforgeeks.org/dsa/inversion-count-in-array-using-merge-sort/)

```
class Solution {
    static int merge(int arr[],int l,int m,int r){
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
         int i=0;
        int j=0;
        int k=l;
        int count=0;
        while(i<n1 && j<n2){
           if(left[i]<=right[j]){
               arr[k]=left[i];
               i++;
               k++;
           }
           else{
               arr[k]=right[j];
               j++;
               k++;
               count+=(n1-i);
           }
        }
        while(i<n1){
            arr[k++]=left[i++];
        }
        while(j<n2){
            arr[k++]=right[j++];
        }
        return count;
    }
    static int merge_sort(int arr[],int l,int r){
        int res=0;
        if(l<r){
            int m=l+(r-l)/2;
           res+= merge_sort(arr,l,m);
           res+=merge_sort(arr,m+1,r);
           res+=merge(arr,l,m,r);
        }
        return res;
    }
    public int inversionCount(int arr[]) {
        int res=merge_sort(arr,0,arr.length-1);
        return res;
    }
}
```

# complexity analysis

Time:O(n logn)

Space:O(n)
