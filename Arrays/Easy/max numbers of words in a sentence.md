# maximum number of words in a sentence

[Problem Link](https://leetcode.com/problems/maximum-number-of-words-found-in-sentences/)

# Approach I
traverse through every sentence in array
count number of spaces return number of words are spaces+1

```Java
class Solution {
    public int mostWordsFound(String[] sentences) {
        int arr[]=new int[sentences.length];
        for(int i=0;i<sentences.length;i++){
            String s=sentences[i];
            int count=0;
            for(int j=0;j<s.length();j++){
                char ch=s.charAt(j);
                if(ch==' '){
                    count++;
                }
            }
            arr[i]=count+1;
        }
        int max=arr[0];
        for(int i=0;i<sentences.length;i++){
            if(max<arr[i])
            max=arr[i];
        }
        return max;
        }
    }
```
# complexity analysis

time complexity:O(N)

