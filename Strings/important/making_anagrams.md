# Making anagrams

[Problem Link](https://www.hackerrank.com/challenges/ctci-making-anagrams/problem?isFullScreen=true&h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)


```
class Result {

    /*
     * Complete the 'makeAnagram' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. STRING a
     *  2. STRING b
     */

    public static int makeAnagram(String a, String b) {
    // Write your code here
      int freq[]=new int[26];
       for(int i=0;i<a.length();i++){
        freq[a.charAt(i)-'a']++;
       }
       for(int i=0;i<b.length();i++){
        freq[b.charAt(i)-'a']--;
       }
       int total=0;
       for(int count:freq){
        total+=Math.abs(count);
       }
       return total;
    }

}

```


# Complexities

Time:O(N)

Space:O(26)
