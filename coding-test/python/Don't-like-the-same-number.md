
#### 🥏 Programmers
# [같은 숫자는 싫어](https://school.programmers.co.kr/learn/courses/30/lessons/12906?language=python3)
`level 1` , `stack/queue`

### 문제 설명

> 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. <br>
> arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다. <br>
> arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.


#### Constraints:
- 배열 arr의 크기 : 1,000,000 이하의 자연수
- 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수

<br><br>

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


~~~python
from itertools import groupby

def solution(arr):
    return [digit for digit, group in groupby(arr)]
~~~

## 해설 

groupby 메서드를 사용.

digit은 그룹으로 묶인 원소.
group은 그룹에 담긴 리스트이다. 이 코드에서는 group은 사용하지 않음

<br>

