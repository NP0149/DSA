# Jewels and stones

[Problem Link](https://leetcode.com/problems/jewels-and-stones/submissions/1538258738/)

# Approach I

 Just compare every character of string stones with every character of jewels when the two characters become equal then increase count and at
 last just return the count

 ```Java
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        int count=0;
        for(int i=0;i<stones.length();i++){
            char c1=stones.charAt(i);
            for(int j=0;j<jewels.length();j++){
               char c2=jewels.charAt(j);
               if(c1==c2){
                count++;
               }
            }
        }
        return count;
    }
}
```
# Complexities

time complexity:O(N^2);

space complexity:O(1);
 
