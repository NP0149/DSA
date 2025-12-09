# To convert Infix to postfix

## 1) if the characters in a string are alphabet(Small or Caps) or 0-9 just append them to new string


 ## 2) if you encounter a '(' the elements after if it is a operands need to be added to the new string or if they are operators need to be pushed into the stack


3)when we are pushing elements into the stack mainly need to follow 3 steps
--

  1) if the top of the stack has less precedence than the character that need to be pushed ,then just push the character

  2) if the top of the stack has higher precedence than the top,then first pop the top of the stack and then push the element into the stack

  3) if the top of the stack has same precedence that equals to the precedence of the character that need to be pushed then pop top of the stack and then push the character into the stack

## 4)at last if the string traversal completed then just pop out the all the elements from the stack
