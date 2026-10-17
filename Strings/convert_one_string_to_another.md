# converting one string to another

[Problem Link](https://www.geeksforgeeks.org/problems/check-if-it-is-possible-to-convert-one-string-into-another-with-given-constraints4116/1)



## start i and j at 0 and then traverse both the strings if until they found a character which is not a space need to iterate after that 

## if one reached the end the other did not so it is a false condition and here we are considering the sequence should be same so that characters in the both need to be the

## same character and traverse in the array 


```
class Solution {
    public boolean isItPossible(String s1, String s2) {
      if(s1.length()!=s2.length()){
          return false;
      }
        int n=s1.length();
        int i=0;
        int j=0;
        while(i<n && j<n){
            while(i<n && s1.charAt(i)=='#'){
                i++;
            }
            while(j<n && s2.charAt(j)=='#'){
                j++;
            }
            if(i==n || j==n){
                return i==n && j==n;
            }
            if(s1.charAt(i)!=s2.charAt(j)){
                return false;
            }
            if(s1.charAt(i)=='A' && j>i){
                return false;
            }
            if(s2.charAt(j)=='B' && j<i){
                return false;
            }
            i++;
            j++;
        }
        while(i<n && s1.charAt(i)=='#'){
            i++;
        } 
        while(j<n && s2.charAt(j)=='#'){
            j++;
        }
        return i==n && j==n;
    }
};
```


# Complexity

Time:O(n)

Space:O(1)
