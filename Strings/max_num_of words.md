```java
class Solution {
    public int mostWordsFound(String[] sentences) {
        int barr[]=new int[sentences.length];
        for(int i=0;i<sentences.length;i++){
            String s=sentences[i];
            int count=0;
            for(int j=0;j<s.length();j++){
                char ch=s.charAt(j);
                if(ch==' '){
                    count++;
                }
            }
            barr[i]=count+1;
        }
         int max=barr[0];
        for(int i=0;i<barr.length;i++){
            if(max<barr[i])
            max=barr[i];
         
        }
        return max;
        }
    }
```
