# Minimum difference between highest and lowest

[Problem Link](https://leetcode.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores/)


# Approach-I

1)we need to sort the array 

2)we need to find the subarrays and in them we need to find the minimum and max value and need to find the difference 
store the value in temp,return the minimum difference

```
class Solution {
    public int minimumDifference(int[] arr, int k) {
        int mini = Integer.MAX_VALUE;
        int n = arr.length;
        int l = 0;
        int r = n - 1;
        int minim=Integer.MAX_VALUE;
        int maxi = Integer.MIN_VALUE;
        int ans = 0;
        if (n == 1) {
            // System.out.println("");
            return 0;
        }
        Arrays.sort(arr);
        for (int i = 0; i < n - k + 1; i++) {
            int j = i + k - 1;
            int temp = 0;
            int prev = 0;
            for (int t = i; t <= j; t++) {
                maxi = Math.max(maxi, arr[t]);
                mini = Math.min(mini, arr[t]);
                //System.out.print(arr[t]+" ");

            }
            temp=maxi-mini;
            minim=Math.min(temp,minim);

        //    System.out.println();
        //    System.out.println("mini="+mini);
        //    System.out.println("maxi="+maxi);
            mini=Integer.MAX_VALUE;
            maxi=Integer.MIN_VALUE;
        }
        return minim;
    }
    }
```

# COMPLEXITY ANALYSIS

Time:O(N^2);

Space:O(1);


# Approach-II

when we are sorting the highest and lowest becomes 0 and n-1 elements so directly find the difference between i and j


```
class Solution {
    public int minimumDifference(int[] arr, int k) {
     int n=arr.length;
     Arrays.sort(arr);
     int temp=Integer.MAX_VALUE;
     int sub=0;
     for(int i=0;i<n-k+1;i++){
        int j=i+k-1;
     sub=arr[j]-arr[i];
      temp=Math.min(sub,temp);
     }

     return temp;
    }
}

```

# Complexity Analysis

time:O(nlogn);

Space:O(1);


# SLIDING WINDOW APPROACH

```
public class scoresdiff{
    public static int finddiff(int arr[],int k) {
        int n = arr.length;
        Arrays.sort(arr);
        int temp = Integer.MAX_VALUE;
        int sub = 0;
        int j = 0;
        int l = 0;
        for (int r = 0; r < n; r++) {
            if (r-l == k) {
                l++;
            }
            if (r-l+ 1 == k) {
                temp = Math.min(temp, Math.abs(arr[l] - arr[r]));
            }
        }
        return temp;
    }
```

# Complexity Analysis

time:O(nlogn);

Space:O(1);


