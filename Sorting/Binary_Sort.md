# Binary Sort

```
 public static void binary_sort(int arr[],int n){
        for(int i=0;i<n;i++ ){
      boolean swapped=false;
            for(int j=0;j<n-i-1;j++){
                if(arr[j]>arr[j+1]){
                    int temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                  swapped=true;
                }
            }
         if(!swapped){
          break;
        }
    }
```

# Complexities

Time:

average and worst cases:O(n^2);

best case:O(n);

Space:O(1)
