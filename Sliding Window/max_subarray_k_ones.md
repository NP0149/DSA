# Maximum length of subarray that contains only k number of ones

# Approach-I

there is an array in which we need to find max length sub array that contains only k number of ones

```
import java.util.*;
public class max_k {
    public static int fun(int arr[], int k) {
        int n = arr.length;
        int l = 0;
        int temp = 0;
        int ans = -1;
        for(int i=0;i<n;i++){
            if(arr[i]==1){
                temp++;
            }
            while(temp>k){
                if(arr[l]==1){
                    temp--;
                }
                l++;
            }
            ans=Math.max(ans,i-l+1);
    }
        return ans;
}

    public static void main(String[] args) {
        int arr[]={12,1,3,1,1,6,7,1,8,1};
        int k=2;
        System.out.println(fun(arr,k));
    }
}
```
# Complexities

Time:O(n)

Space:O(1)
