# Construct minimum bitwise array

[Problme link](https://leetcode.com/problems/construct-the-minimum-bitwise-array-i/?envType=daily-question&envId=2026-01-20)

```
class Solution {
    public int[] minBitwiseArray(List<Integer> nums) {
        int ans[]=new int[nums.size()];
        Arrays.fill(ans,-1);
        for(int i=0;i<nums.size();i++){
            for(int j=0;j<nums.get(i);j++){
                if((j|(j+1))==nums.get(i)){
                    ans[i]=j;
                    break;
                }
            }
        }
        return ans;
    }
}
```
# Complexity Anlaysis

Time:O(n*n)

Space:O(1)
