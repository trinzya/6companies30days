# Bulls And Cows
[LeetCode Bulls Cows](https://leetcode.com/problems/bulls-and-cows/)


You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.

 

### Example 1:

Input: secret = "1807", guess = "7810"
Output: "1A3B"
Explanation: Bulls are connected with a '|' and cows are underlined:
"1807"
  |
"7810"


### Solution
```Python
import collections
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        bulls=0
        cows=0
        s= collections.Counter(secret)
        d={}
        for i in range(len(secret)):
            if(secret[i]==guess[i]):
                bulls=bulls+1
                if(secret[i] not in d.keys()):
                    d[secret[i]]=1
                else:
                    d[secret[i]]=d[secret[i]]+1
        for i in guess:
            if(i in secret and s[i]>0):
                if(i not in d.keys()):
                    cows=cows+1
                else:
                    if(d[i]==0):
                        cows=cows+1
                    else:
                        d[i]=d[i]-1
                s[i]=s[i]-1
        print(d)
        return str(bulls)+'A'+ str(cows)+'B'
            
