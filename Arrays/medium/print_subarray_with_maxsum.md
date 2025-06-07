# Print the subarray with max sum

```
   public static int find(int arr[]){
        int n=arr.length;
        int maxsum=Integer.MIN_VALUE;
        int sum=0;
        int j=0;
        int start=0;
        int end=0;
        for(int i=0;i<n;i++) {
            sum += arr[i];
            if (sum > maxsum) {
                maxsum=sum;
                end = i;
            }
            if (sum < 0) {
                sum = 0;
                start += i;
            }
        }
        for(int i=start+1;i<end;i++){
            System.out.print(arr[i]+" ");
        }
        System.out.println();
        return maxsum;
    }
```
# Complexity Analysis

Time:O(n);

Space:O(1);
