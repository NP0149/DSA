# Move Zeroes to the end of the array

[Problem Link](https://leetcode.com/problems/move-zeroes/description/)


# Approach-I

```
class Solution {
    public void moveZeroes(int[] arr) {
        int n=arr.length;
        try{
        for(int i=0;i<n;i++){
            int j=0;
            if(arr[i]==0){
                j=i+1;
                while(arr[j]==0){
                    j++;
                }
            
            int temp=arr[i];
            arr[i]=arr[j];
            arr[j]=temp;
            }
        }
    }catch(Exception e){

    }
}
}
```

# Complexties

Time:O(n^2)//in worst case and O(n) in other approaches

Space:O(1)

# Approach-II

```
class Solution {
    public void moveZeroes(int[] arr) {
        int n=arr.length;
        int j=0;
        for(int i=0;i<n;i++){
            if(arr[i]!=0){
                arr[j++]=arr[i];
            }
        }
        while(j<n){
            arr[j++]=0;
        }
        
}
}
```

# Complexities

Time:O(n);//in all cases

Space:O(1)
