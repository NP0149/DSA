# Alternating Characters

[Problem Link](https://www.hackerrank.com/challenges/alternating-characters/problem?isFullScreen=true&h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)


```
  public static int alternatingCharacters(String s) {
    // Write your code here
        int count=0;
        int counta=0;
        int countb=0;
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='A' && counta>0){
                count++;
            }
            else if(s.charAt(i)=='B' && countb>0){
                count++;
            }
            else if(s.charAt(i)=='A' && counta==0){
                counta++;
                countb=0;
            }
            else if(s.charAt(i)=='B' && countb==0){
                countb++;
                counta=0;
            }
        }
        return count;
    }

}
```

# Complexity Analysis

Time:O(N)

Space:O(1)
