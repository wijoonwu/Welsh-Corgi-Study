#### ๐ณ๏ธโ๐ Leet Code
## [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)
> Easy

### ๋ฌธ์  ์ค๋ช

> Given two strings s and t, return true if s is a subsequence of t, or false otherwise.
A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters 
without disturbing the relative positions of the remaining characters. 
(i.e., "ace" is a subsequence of "abcde" while "aec" is not).

#### Example 1:
~~~
Input: s = "abc", t = "ahbgdc"
Output: true
~~~

#### Example 2:
~~~
Input: s = "axc", t = "ahbgdc"
Output: false
~~~

#### Constraints:
- 0 <= s.length <= 100
- 0 <= t.length <= 10^4
- s and t consist only of lowercase English letters.


<br><br>

## ๐ฉ๐ปโ๐ป ๋ฌธ์  ํ์ด

##### ๐๐ปโโ๏ธ ์์ฑ์ : ๊น์ค๊ฒธ([@yoongyum](github.com/yoongyum))


~~~python
from collections import deque


def isSubsequence(self, s: str, t: str) -> bool:
    st = deque(list(s))
    for i in t:
        if len(st) == 0:
            return True
        if st[0] == i:
            st.popleft()
    return len(st) == 0
~~~
### ๐ฌ ์ฝ๋ ํด์ค
1. ๋ฌธ์์ด s๋ฅผ deque๋ก ๋ง๋ ๋ค.
2. t๊ธ์์ ๋งํผ ์ฌ์ดํด์ ๋๋ฆฐ๋ค.
3. deque์ ์ฒซ๋ฒ์งธ ์ธ๋ฑ์ค์ ์ํ๋ฒณ์ด ๊ฐ์ผ๋ฉด deque์ ๋งจ์์ ์ ๊ฑฐํ๋ค.
4. deque๊ฐ ๋น ์ํ๊ฐ ๋๋ฉด True, ์๋น๋ค๋ฉด False

### ๐ก ์๋ก ์๊ฒ๋ ์ 
#### ๋ค๋ฅธ์ฌ๋ ํ์ด
```py
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i, j = 0, 0
        
        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i += 1
            j += 1
            
        return i == len(s)
```
๋ค๋ฅธ ์ฌ๋๋ค์ ํฌํฌ์ธํฐ ์๊ณ ๋ฆฌ์ฆ์ผ๋ก ํ์์ง๋ง, ๋ด ์ฝ๋๋ ์๋๊ฐ ์์๊ถ์ด๋ผ ์๊ด์๋ ๋ฏํ๋ค.
