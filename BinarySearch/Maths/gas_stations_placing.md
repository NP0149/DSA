# Gas Stations Placing

[Problem Link](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1)


```
class Solution {
    public double minMaxDist(int[] arr, int k) {
        // code here
        PriorityQueue<int[]> pq=new PriorityQueue<>((a,b)->Double.compare((double)b[0]/b[1],(double)a[0]/a[1]));
        for(int i=0;i<arr.length-1;i++){
            int dis=arr[i+1]-arr[i];
            pq.add(new int[]{dis,1});
        }
        while(k>0){
            int curr[]=pq.poll();
            int dis=curr[0];
            int parts=curr[1];
            parts++;
            pq.add(new int[]{dis,parts});
            k--;
        }
        double max=Double.MIN_VALUE;
        while(!pq.isEmpty()){
            int curr[]=pq.poll();
            max=Math.max(max,(double)curr[0]/curr[1]);
        }
        
        return max;
    }
}
```

# Optimal Approach

```
class Solution {
    static double find_min(int arr[],int k,double mid){
        int count=0;
        double diff;
        for(int i=1;i<arr.length;i++){
            diff=arr[i]-arr[i-1];
            if(diff>mid){
                int f=(int)(diff/mid);
                count+=f;
                if(count>k){
                    return 0;
                }
            }
        }
        return 1;
    }
    public double minMaxDist(int[] arr, int t) {
        if(arr.length==1 && t>=1){
            return 0;
        }
        // code here
        double low=0;
        int n=arr.length;
        double high=arr[n-1]-arr[0];
        double ans=-1;
        while(high-low>=0.000001){
            double mid=low+(high-low)/2;
            double k=(double)find_min(arr,t,mid);
            if(k==1){
                ans=mid;
                high=mid-0.000001;
            }
            else{
                low=mid+0.000001;
            }
        }
        return ans;
    }
}

```

# Complexities

Time:O(n)

Space:O(1)
