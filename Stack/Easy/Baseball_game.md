# BaseBall Game Scoring

[Problem Link](https://leetcode.com/problems/baseball-game/submissions/1716042389/)

# Approach-I

1)
    An integer x
  
   Record a new score of x.
  
    '+'.
  
  Record a new score that is the sum of the previous two scores.
  
    'D'.
  
   Record a new score that is the double of the previous score.
  
    'C'.
  
  Invalidate the previous score, removing it from the record.


  ```
  class Solution {
    public int calPoints(String[] op) {
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<op.length;i++){
            String s=op[i];
            if(s.equals("C")){
                st.pop();
            }
            else if(s.equals("D")){
                int num1=st.pop();
                int num2=2*num1;
                st.push(num1);
                st.push(num2);
            }
            else if(s.equals("+")){
                int num1=st.pop();
                int num2=st.pop();
                int num3=num1+num2;
                st.push(num2);
                st.push(num1);
                st.push(num3);
            }
            else{
                st.push(Integer.parseInt(s));
            }
        }
        int sum=0;
        while(!st.isEmpty()){
        sum+=st.pop();
        }
        return sum;
    }
  }
  ```
  # Complexity Analysis

  Time:O(n)

  Space:O(n)
