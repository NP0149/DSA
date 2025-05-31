# Insertion Sort

```
  public static void insertion_sort(int arr[],int n) {
        for(int i=0;i<n;i++){
            int j=i;
            while(j>0 && arr[j-1]>arr[j]){
                int temp=arr[j-1];
                arr[j-1]=arr[j];
                arr[j]=temp;
                j--;
            }
        }
    }
```

# complexities

Time:

best:O(n);

average and best case:O(n^2);

Space:
O(1)
