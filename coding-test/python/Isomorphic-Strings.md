#### 🏳️‍🌈 Leet Code
## [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)
> Easy

### 문제 설명

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

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


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
### 💬 코드 해설
> 1. 문자열 s, t 각각 해쉬를 만들어준다.
> 2. 반복문으로 한자리씩 확인한다.
> 3. 현재 알파벳이 이미 각 해쉬에 있는 지 확인 후 존재한다면, 서로 반대되는 알파벳과 비교 후 다르면 False를 리턴
> 4. 반복문이 문제없이 끝나면 True 리턴

### 💡 새로 알게된 점

해쉬를 쓰지 않고도 풀 수 있다...

#### 다른사람 코드
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
`s1.append(s.index(s[i]))` 이 부분에 각 자리별로 어떻게 들어가는 지 출력해보면, <br>
p 0 <br>
a 1 <br>
p 0 <br>
e 3 <br>
r 4 
<br>
이런 식으로 나오는데, 이러면 굳이 해쉬를 쓰지 않고도 `s`와 `t`가 isomorphic 한 형태인지 알 수 있다. 👍👍👍

