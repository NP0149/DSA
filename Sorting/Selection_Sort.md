# Selection Sort

```
public class selectionsort {
    public static void select_sort(int arr[],int n){
        for(int i=0;i<n-1;i++){
            int minidx=i;
            for(int j=i;j<n;j++){
                if(arr[j]<arr[minidx]){
                    minidx=j;
                }
            }
            int temp=arr[i];
            arr[i]=arr[minidx];
            arr[minidx]=temp;
        }
    }
```

# Complexities

Time:O(n^2)//best,avg,worst(in all cases)

Space:O(1)
