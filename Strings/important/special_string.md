# Special String

[Problem Link](https://www.hackerrank.com/challenges/special-palindrome-again/problem?isFullScreen=true&h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

```

class group{
    char ch;
    int count;
    group(char ch,int count){
        this.ch=ch;
        this.count=count;
    }
}
public class Solution {
    // Complete the substrCount function below.
    static long substrCount(int n, String s) {
   List<group> li=new ArrayList<>();
   int i=0;
   while(i<s.length()){
    int j=i;
    while(j<s.length() && s.charAt(i)==s.charAt(j)){
        j++;
    }
    li.add(new group(s.charAt(i),j-i));
    i=j;
   }
   long total=0;
   for(int t=0;t<li.size();t++){
    int count=li.get(t).count;
    total+=count*(count+1)/2;
   }
   for(int t=1;t<li.size()-1;t++){
    group prev=li.get(t-1);
    group curr=li.get(t);
    group next=li.get(t+1);
    if(curr.count==1 && prev.ch==next.ch){
        total+=Math.min(prev.count,next.count);
    }
   }
   
   return total;
   
    }
```
