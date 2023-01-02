# Evaulate Reverse Polish Notation

[LeetCode Evaulate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) 


You are given an array of strings tokens that represents an arithmetic expression in a [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return an integer that represents the value of the expression.

**Note that**:

- The valid operators are '+', '-', '*', and '/'.
- Each operand may be an integer or another expression.
- The division between two integers always truncates toward zero.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in a reverse polish notation.
- The answer and all the intermediate calculations can be represented in a 32-bit integer. 


### Example
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9 


### Solution
``` Python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        PostFixStack =[]
        for i in tokens:
            if(i == '+' or i=='-' or i=='*' or i=='/' ):
                num1=PostFixStack.pop()
                num2=PostFixStack.pop()
                if(i=='+'):
                    PostFixStack.append(num1+num2)
                elif(i=='-'):
                    PostFixStack.append(num2-num1)
                elif(i=='*'):
                    PostFixStack.append(num1*num2)
                elif(i=='/'):
                    PostFixStack.append(int(num2/num1))
            else:
                PostFixStack.append(int(i))
        return PostFixStack.pop()
        
 
