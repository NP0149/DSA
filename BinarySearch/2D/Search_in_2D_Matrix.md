# Search in a 2D matrix

[Problem Link](https://leetcode.com/problems/search-a-2d-matrix/submissions/1699115060/)

# Approach-I(Better)

1)As the elements in the matrix are sorted so we can use binary search,by pasing evry row to the function and by reducing number of operations
so that it will become efficient

```
class Solution {
    public static int find(int []arr,int target){
        int m=arr.length;
        int low=0;
        int high=m-1;
        if(arr[m-1]<target){
            return -1;
        }
        while(low<=high){
            int mid=(low+high)/2;
            if(target==arr[mid]){
                 return 1;
            }
            else if(target>arr[mid]){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return -1;
    }
    public boolean searchMatrix(int[][] mat, int target) {
        int ans=-1;
        for(int i=0;i<mat.length;i++){
            int k=find(mat[i],target);
             if(k==-1){
                continue;
             }
             else{
                ans=find(mat[i],target);
                if(ans==1){
                    return true;
                }
             }
        }
        return false;
    }
}
```
# Complexities

Time:O(n*log m)

Space:O(1)

# Approach-II(BEST)

1)just convert 2D matrix into 1D by flattening it and then search the way we do linear serach 

2)we can find low=0 and high=n(no.of rows)*m(no.of cols)-1 adn then to find the row=mid/cols and column=mid%cols
and then apply linear search

```
class Solution {
    public boolean searchMatrix(int[][] mat, int target) {
        int n=mat.length;
        int m=mat[0].length;
        int low=0;
        int high=n*m-1;
        while(low<=high){
            int mid=(low+high)/2;
            int row=mid/m;
            int col=mid%m;
            int midval=mat[row][col];
             if(target==midval){
               return true;
            }
            else if(target<midval){
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return false;
    }
}
```

# Complexities

Time:O(log(m*n));

Space:O(1)
