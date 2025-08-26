# Single number II
[Problem Link](https://leetcode.com/problems/single-number-ii/description/)

# Approach-I(Brute)

1)traverse through all bits from 0 to 31(total 32 bits) and check every time whether that particular bit is set or not if the number of ones set are the multiple of 3 then unset the bit in your new number,if not set the number

```
 static int find_another(int arr[]){
        int res=0;
        for(int i=0;i<32;i++){
            int count=0;
            for(int num:arr){
                if(((num>>i)&1)==1){
                    count++;
                }
            }
            if(count%3!=0){
                res=res|(1<<i);
            }
        }
        return res;
    }
```

# Complexity Analysis

Time:O(32*N)

Space:O(1)

# Approach-II(Better)

1)every element in the array repeats thrice except one so we need to find that one particular number

2) every time compare arr[i] and arr[i-1] and then jump by 3 steps

```
class Solution {
    public int singleNumber(int[] arr) {
        Arrays.sort(arr);
        int n=arr.length;
        for(int i=1;i<arr.length;i=i+3){
            if(arr[i]!=arr[i-1]){
                return arr[i-1];
            }
        }
        return arr[n-1];
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)


# Approach-III(Optimal)

1)it is the buckets approach you need to consider two buckets as for this problem and then name those buckets as ones and twos

2)add the number into ones only if it is not in twos

3)add the number into twos only if it is not in ones

```
  static int find_xor(int arr[]){
        int ones=0;
        int twos=0;
        for(int i=0;i<arr.length;i++){
            ones=(ones^arr[i])&~twos;
            twos=(twos^arr[i])&~ones;
        }
        return ones;
    }

```

# Complexity Analysis

Time:O(N)

Space:O(1)
