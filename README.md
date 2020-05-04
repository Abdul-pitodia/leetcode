# leetcode
my codes for may challenge
-----------------------------------------------------------------------------------------------------------------------
## 1 - JEWELS AND STONES 
========================
'''
You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:

Input: J = "aA", S = "aAAbbbb"
Output: 3

'''
##CODE:
```
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        self.J = J
        self.S = S
        stone_lst = []
        lst = []
        for stone in self.S:
            count = 0
            for i in range(len(J)):
                if (stone == J[i]):
                    stone_lst.append(stone)
                else:
                    continue           
        stone_lst = list(set(stone_lst))
        for alp in stone_lst:
            cnt = 0
            for i in range(len(self.S)):
                if (alp == self.S[i]):
                    cnt += 1
            lst.append(cnt)
        return sum(lst)
```  
--------------------------------------------------------------------------------------------------------
##2 RANSOM NOTE
==============
Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

Note:
You may assume that both strings contain only lowercase letters.

canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true

----
##CODE (not optimal)
----
```
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        self.ransomNote = ransomNote
        self.magazine = magazine
        rn = set(self.ransomNote)
        mg = set(self.magazine)
        dt_mg = dict()
        dt_rn = dict()
        flag = 1        
        if (len(rn) != 0):
            for alp in mg:
                cnt = 0
                for i in range(len(self.magazine)):
                    if (alp == self.magazine[i]):
                        cnt = cnt + 1
                dt_mg[alp] = cnt               
            for alp in rn:
                cnt = 0
                for i in range(len(self.ransomNote)):
                    if(alp == self.ransomNote[i]):
                        cnt = cnt + 1
                dt_rn[alp] = cnt
            for key in dt_rn.keys():
                if key in dt_mg.keys():
                    if(dt_rn[key] > dt_mg[key]):
                        flag = 0
                        break
                    else:
                        flag = 1
                else:
                    flag = 0
                    break        
            if (flag == 0):
                return False
            else:
                return True
        else:
            return True

```
-----------------------------------------------------------------------------------------------------------------

##3 NUMBER COMPLEMENT 
Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

 
Example 1:

Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.


--
##CODE
--
```
class Solution:
    def findComplement(self, num: int) -> int:
        bn = bin(num)
        bn_lst = bn[2:]
        nm_lst = []
        for i in range(len(bn_lst)):
            if (bn_lst[i] == '1'):
                nm_lst.append(0)
            else:
                nm_lst.append(1)      
        res = "".join(map(str,nm_lst))
        res = int(res,2)
        return res
```
------------------------------------------------------------------------------------------------------------------------
