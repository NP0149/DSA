
[Problem Link](https://www.hackerrank.com/challenges/sherlock-and-valid-string/problem?isFullScreen=true&h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

```
class Result {

    /*
     * Complete the 'isValid' function below.
     *
     * The function is expected to return a STRING.
     * The function accepts STRING s as parameter.
     */

    public static String isValid(String s) {
    // Write your code here
    HashMap<Character,Integer> hm=new HashMap<>();
    for(int i=0;i<s.length();i++){
        hm.put(s.charAt(i),hm.getOrDefault(s.charAt(i),0)+1);
    }
    HashMap<Integer,Integer> freqmap=new HashMap<>();
    for(int freq:hm.values()){
        freqmap.put(freq,freqmap.getOrDefault(freq,0)+1);
    }
    if(freqmap.size()==1){
        return "YES";
    }
    if(freqmap.size()>2){
        return "NO";
    }
    List<Integer> li=new ArrayList<>(freqmap.keySet());
    int freq1=li.get(0);
    int freq2=li.get(1);
    int count1=freqmap.get(freq1);
    int count2=freqmap.get(freq2);
    if(freq1==1 && count1==1){
        return "YES";
    }
    if(freq2==1 && count2==1){
        return "YES";
    }
    if(freq1-freq2==1 && count1==1){
        return "YES";
    }
    if(freq2-freq1==1 && count2==1){
        return "YES";
    }
    return "NO";    
    }
    

}

```


# Complexity


Time:O(N)

Space:O(1)
