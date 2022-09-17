#### 🏳️‍🌈 Leet Code
## [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)
> Easy

### 문제 설명

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

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


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
### 💬 코드 해설
1. 문자열 s를 deque로 만든다.
2. t글자수 만큼 사이클을 돌린다.
3. deque의 첫번째 인덱스와 알파벳이 같으면 deque의 맨앞을 제거한다.
4. deque가 빈 상태가 되면 True, 안빈다면 False

### 💡 새로 알게된 점
#### 다른사람 풀이
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
다른 사람들은 투포인터 알고리즘으로 풀었지만, 내 코드도 속도가 상위권이라 상관없는 듯하다.
