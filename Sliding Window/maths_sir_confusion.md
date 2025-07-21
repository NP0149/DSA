# Maths sir confusion

[Problem Link](https://leetcode.com/problems/maximize-the-confusion-of-an-exam/description/)

# Approach-I

So you can flip both 'T' to 'F' and 'F' to 'T' so we can take both count of true and count of false and then min of count of true and count of false
if greater than k,then we need to check the l pos and then need to decrease that particular count

```
class Solution {
    public int maxConsecutiveAnswers(String str, int k) {
        int n=str.length();
        int cntf=0;
        int cntt=0;
        int l=0;
        int ans=-1;
        for(int i=0;i<n;i++){
            char ch=str.charAt(i);
           if(ch=='T'){
            cntt++;
           }
           else{
            cntf++;
           }
           while(Math.min(cntt,cntf)>k){
            if(str.charAt(l)=='T'){
                cntt--;
            }
            else{
                cntf--;
            }
            l++;
           }
       ans=Math.max(ans,i-l+1);
           }
        
        return ans;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)
