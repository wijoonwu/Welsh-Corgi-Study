
#### ๐ฅ Programmers
# [๊ฐ์ ์ซ์๋ ์ซ์ด](https://school.programmers.co.kr/learn/courses/30/lessons/12906?language=python3)
`level 1` , `stack/queue`

### ๋ฌธ์  ์ค๋ช

> ๋ฐฐ์ด arr์์ ์ฐ์์ ์ผ๋ก ๋ํ๋๋ ์ซ์๋ ํ๋๋ง ๋จ๊ธฐ๊ณ  ์ ๋ถ ์ ๊ฑฐํ๋ ค๊ณ  ํฉ๋๋ค. <br>
> arr = [1, 1, 3, 3, 0, 1, 1] ์ด๋ฉด [1, 3, 0, 1] ์ return ํฉ๋๋ค. <br>
> arr = [4, 4, 4, 3, 3] ์ด๋ฉด [4, 3] ์ return ํฉ๋๋ค.


#### Constraints:
- ๋ฐฐ์ด arr์ ํฌ๊ธฐ : 1,000,000 ์ดํ์ ์์ฐ์
- ๋ฐฐ์ด arr์ ์์์ ํฌ๊ธฐ : 0๋ณด๋ค ํฌ๊ฑฐ๋ ๊ฐ๊ณ  9๋ณด๋ค ์๊ฑฐ๋ ๊ฐ์ ์ ์

<br><br>

## ๐ฉ๐ปโ๐ป ๋ฌธ์  ํ์ด

##### ๐๐ปโโ๏ธ ์์ฑ์ : ๊น์ค๊ฒธ([@yoongyum](github.com/yoongyum))


~~~python
from itertools import groupby

def solution(arr):
    return [digit for digit, group in groupby(arr)]
~~~

## ํด์ค 

groupby ๋ฉ์๋๋ฅผ ์ฌ์ฉ.

digit์ ๊ทธ๋ฃน์ผ๋ก ๋ฌถ์ธ ์์.
group์ ๊ทธ๋ฃน์ ๋ด๊ธด ๋ฆฌ์คํธ์ด๋ค. ์ด ์ฝ๋์์๋ group์ ์ฌ์ฉํ์ง ์์

<br>

