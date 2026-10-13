# Common child

[Problem Link](https://www.hackerrank.com/challenges/common-child/problem?isFullScreen=true&h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)


# remember the word common child

```
/*
     * Complete the 'commonChild' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. STRING s1
     *  2. STRING s2
     */

```

```
   public static int commonChild(String s1, String s2) {
     int dp[][]=new int[s1.length()+1][s2.length()+1];
     for(int i=1;i<=s1.length();i++){
        for(int j=1;j<=s2.length();j++){
            if(s1.charAt(i-1)==s2.charAt(j-1)){
                dp[i][j]=1+dp[i-1][j-1];
            }
            else{
                dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
            }
        }
     }
     return dp[s1.length()][s2.length()];
     
    }
```
