# Rolling characters in String based on the given adjacent array named roll

[Problem Link](https://www.geeksforgeeks.org/problems/roll-the-characters-of-a-string2127/1)

## here i am considering a shift array ,by that i am considering like how many times that particular index character is getting rolled by adjacent characters

## so finding newpostion from orginal and then finding new character and then converting string into mutable array and then putting the newchar int that pos

## converting array into string and then returning

```
class Solution {
    public String findRollOut(String s, int[] roll) {
       int shifts[]=new int[s.length()];
       for(int i=0;i<roll.length;i++){
           shifts[roll[i]-1]++;
       }
       char arr[]=s.toCharArray();
       int max_shift=0;
       for(int i=s.length()-1;i>=0;i--){
           int org=s.charAt(i)-'a';
           max_shift+=shifts[i];
           int newpos=(org+max_shift)%26;
//important
           char newchar=(char)(newpos+'a');
           arr[i]=newchar;
       }
       String ans=new String(arr);
       return ans;
    }
}
```
