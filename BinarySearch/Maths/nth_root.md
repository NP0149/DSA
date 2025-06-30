# Nth root of a number

```
class Solution {
    public static int fun(int n,int mid){
        int ans=1;
        int i=1;
        while(i<=n){
            ans*=mid;
            i++;
        }
        return ans;
    }
    public int NthRoot(int n, int m) {
        int low=1;
        int high=m;
        while(low<=high){
            int mid=(low+high)/2;
            int find=fun(n,mid);
            if(find==m){
                return mid;
            }
            else if(find<=m){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return -1;
    }
}

```
# Complexities

Time:O(log N)

Space:O(1)
