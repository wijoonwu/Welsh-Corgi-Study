#### π³οΈβπ Leet Code
## [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)
> Easy

### λ¬Έμ  μ€λͺ

> Given two strings s and t, determine if they are isomorphic.
>Two strings s and t are isomorphic if the characters in s can be replaced to get t.
>All occurrences of a character must be replaced with another character while preserving the order of characters. 
>No two characters may map to the same character, but a character may map to itself.

#### Example 1:
~~~
Input: s = "egg", t = "add"
Output: true
~~~

#### Example 2:
~~~
Input: s = "foo", t = "bar"
Output: false
~~~

#### Example 3:
~~~
Input: s = "paper", t = "title"
Output: true
 ~~~


#### Constraints:
- 1 <= s.length <= 5 * 10^4
- t.length == s.length
- s and t consist of any valid ascii character.6`

<br><br>

## π©π»βπ» λ¬Έμ  νμ΄

##### ππ»ββοΈ μμ±μ : κΉμ€κ²Έ([@yoongyum](github.com/yoongyum))


~~~python
from collections import defaultdict


def isIsomorphic(s: str, t: str) -> bool:
    shash = defaultdict(str)
    thash = defaultdict(str)
    for i in range(len(s)):  # 5*10_000
        if s[i] in shash:
            if shash[s[i]] != t[i]:
                return False
        elif t[i] in thash:
            if thash[t[i]] != s[i]:
                return False
        else:
            shash[s[i]] = t[i]
            thash[t[i]] = s[i]

    return True
~~~
### π¬ μ½λ ν΄μ€
> 1. λ¬Έμμ΄ s, t κ°κ° ν΄μ¬λ₯Ό λ§λ€μ΄μ€λ€.
> 2. λ°λ³΅λ¬ΈμΌλ‘ νμλ¦¬μ© νμΈνλ€.
> 3. νμ¬ μνλ²³μ΄ μ΄λ―Έ κ° ν΄μ¬μ μλ μ§ νμΈ ν μ‘΄μ¬νλ€λ©΄, μλ‘ λ°λλλ μνλ²³κ³Ό λΉκ΅ ν λ€λ₯΄λ©΄ Falseλ₯Ό λ¦¬ν΄
> 4. λ°λ³΅λ¬Έμ΄ λ¬Έμ μμ΄ λλλ©΄ True λ¦¬ν΄

### π‘ μλ‘ μκ²λ μ 

ν΄μ¬λ₯Ό μ°μ§ μκ³ λ ν μ μλ€...

#### λ€λ₯Έμ¬λ μ½λ
```py
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        s1=[]
        s2=[]
        for i in range(len(s)):   #record the index of the 2 strings and then compare
            s1.append(s.index(s[i]))
            s2.append(t.index(t[i]))
        return s1==s2
```
`s1.append(s.index(s[i]))` μ΄ λΆλΆμ κ° μλ¦¬λ³λ‘ μ΄λ»κ² λ€μ΄κ°λ μ§ μΆλ ₯ν΄λ³΄λ©΄, <br>
p 0 <br>
a 1 <br>
p 0 <br>
e 3 <br>
r 4 
<br>
μ΄λ° μμΌλ‘ λμ€λλ°, μ΄λ¬λ©΄ κ΅³μ΄ ν΄μ¬λ₯Ό μ°μ§ μκ³ λ `s`μ `t`κ° isomorphic ν ννμΈμ§ μ μ μλ€. πππ

