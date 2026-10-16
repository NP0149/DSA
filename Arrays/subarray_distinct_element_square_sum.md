# subarray distinct element sum 

[Problem Link](https://leetcode.com/problems/subarrays-distinct-element-sum-of-squares-i/description/?envType=daily-question&envId=2026-10-15)


# Brute 

## based on the constraints I decided to generate all the subsets and then put them into hashset where we can get the distinct numbers and 
## then getting the square of the size 

```
class Solution {
    public int sumCounts(List<Integer> li) {
        long sum=0;
        for(int i=0;i<li.size();i++){
            for(int j=i;j<li.size();j++){
                HashSet<Integer> hs=new HashSet<>();
                for(int k=i;k<=j;k++){
                  hs.add(li.get(k));
                }
                System.out.print(hs);
                int m=hs.size();
                sum+=(m*m);
            }
        }
        return (int)sum;
    }
}
```


# Complexity

Time:O(n^3)

Space:O(n^2)
