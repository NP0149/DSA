# water bottles

[Problem Link](https://leetcode.com/problems/water-bottles/description/)

# Approach

1)when there are water full bottles then all will be drunk

2)all will be drunk so empty bottles also become total bottles

3)add them to the total drunk and then return it

```
class Solution {
    public int numWaterBottles(int bottles, int numexchange) {
        int totalDrunk = 0;
        int emptybottles = 0;
        
        while (bottles >0) {
            totalDrunk += bottles; // Drink all full bottles
            emptybottles += bottles; // Convert to empty bottles
            
            // Exchange empty bottles for new full bottles
            bottles = emptybottles / numexchange;
            emptybottles = emptybottles % numexchange;
        }
        
        return totalDrunk;

    }
}
```

# complexities

Time complexity:O(N);

space complexity:O(1);
