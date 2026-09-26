[Problem Link](https://www.geeksforgeeks.org/problems/box-stacking/1)

```
class Solution {
    static class box{
        int l,h,w;
        box(int l,int w,int h){
            this.l=l;
            this.w=w;
            this.h=h;
        }
    }
    public int maxHeight(int[] height, int[] width, int[] length) {
     List<box> li=new ArrayList<>();
     for(int i=0;i<height.length;i++){
         li.add(new box(Math.max(width[i],length[i]),Math.min(width[i],length[i]),height[i]));
         li.add(new box(Math.max(width[i],height[i]),Math.min(width[i],height[i]),length[i]));
         li.add(new box(Math.max(length[i],height[i]),Math.min(length[i],height[i]),width[i]));
     }
     Collections.sort(li,(a,b)->{
         if(a.l!=b.l){
             return b.l-a.l;
         }
         return b.w-a.w;
     });
     int dp[]=new int[li.size()];
     int ans=0;
     for(int i=0;i<dp.length;i++){
          dp[i]=li.get(i).h;
         for(int j=0;j<i;j++){
             int take=0;
             if(li.get(i).l<li.get(j).l && li.get(i).w<li.get(j).w){
                 dp[i]=Math.max(dp[i],dp[j]+li.get(i).h);
             }
         }
         ans=Math.max(ans,dp[i]);
     }
     return ans;
    }
}
```
