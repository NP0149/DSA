# Rearrange array elements by sign

[Problem Link](https://leetcode.com/problems/rearrange-array-elements-by-sign/description/)

# Approach-I

1)traverse the array consider two arrays like positive and negative array and then if it is a even position allocate positive array value
if it is negative position then allocate negative array value by using different pointers..

```
class Solution {
    public int[] rearrangeArray(int[] arr) {
        int n=arr.length;
        int pos[]=new int[n/2];
        int neg[]=new int[n/2];
        int j=0;
        int k=0;
        for(int i=0;i<n;i++){
           if(arr[i]<0){
            neg[j++]=arr[i];
           }
           else{
            pos[k++]=arr[i];
           }
        }
        int t=0;
        int m=0;
        for(int i=0;i<n;i++){
            if(i%2==0){
                arr[i]=pos[t++];
            }
            else{
                arr[i]=neg[m++];
            }
        }
        return arr;
    }
}
```

# Complexties

Time:O(n);

Space:O(n);


# Approach-II

```

public static void rearrange(int arr[]) {
        int n = arr.length;
      int pos=0;
      int neg=1;
      int res[]=new int[n];
      for(int i=0;i<n;i++){
          if(arr[i]>0){
              res[pos]=arr[i];
              pos+=2;
          }
          else{
              res[neg]=arr[i];
              neg+=2;
          }
      }
        for(int i=0;i<n;i++){
            System.out.print(res[i]+" ");
        }
    }
```
# Complexties

Time:O(n);

Space:O(n);
