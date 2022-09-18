
#### 🥏 Programmers
# [두 큐 합 같게 만들기](https://school.programmers.co.kr/learn/courses/30/lessons/118667)
`level 2` , `kakao`, `queue`

### 문제 설명

> 문제는 너무 길어서 생략. 위 링크에서 참고 <br>
> 문제 제목이 문제임


#### Constraints:
- 1 ≤ queue1의 길이 = queue2의 길이 ≤ 300,000
- 1 ≤ queue1의 원소, queue2의 원소 ≤ 10^9 

주의: 언어에 따라 합 계산 과정 중 산술 오버플로우 발생 가능성이 있으므로 long type 고려가 필요합니다.

<br><br>

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


~~~python
from collections import deque


def solution(queue1, queue2):
    total = (sum(queue1) + sum(queue2))//2
    if (sum(queue1) + sum(queue2)) % 2 != 0:
        return -1
    q1 = deque(queue1)
    q2 = deque(queue2)
    leftSum = sum(q1)
    rightSum = sum(q2)
    limit1 = len(q1)
    limit2 = len(q2)

    answer = 0
    while True:
        if leftSum == total:
            return answer
        answer += 1
        if leftSum > rightSum:
            val = q1.popleft()
            leftSum -= val
            q2.append(val)
            rightSum += val
        else:
            val = q2.popleft()
            rightSum -= val
            q1.append(val)
            leftSum += val
        if answer > limit1 + limit2 + 2:
            return -1
~~~

## 해설 
0. 두수 합의 중간을 구한다. `total`
1. 두 큐의 합이 홀수이면 바로 종료 
2. 시간 효율성을 위해 `deque`로 변경
3. 초기에 두 큐의 합을 미리 구해놓는다. `leftSum`, `rightSum`
  - 📌이유 : `while`문 안에서 `sum` 함수를 사용하면 시간초과남
4. `while`문 실행 
5. 한쪽 값이 `total` 값과 같아지면 종료
6. 둘 중 합이 큰 쪽에서 빼고 작은 쪽에 더해준다.
7. 아무리 해도 못구하는 경우 `-1`을 반환한다.
  - 못구하는 조건을  `if answer > limit1 + limit2 + 2:`로 짜긴 했는데 왜되는지 모르겠다.

<br>

### 💡 새로 알게된 점
다른 분의 코드인데 

큐를 하나로 합쳐서 하나만 써서

`start`, `end` 투 포인터로 푸신거 같다. 

#### 🍕 다른사람 풀이 코드
```py
def solution(que1, que2):
    queSum = (sum(que1) + sum(que2))
    if queSum % 2:
        return -1
    target = queSum // 2

    n = len(que1)
    start = 0
    end = n - 1
    ans = 0

    cur = sum(que1)
    que3 = que1 + que2
    while cur != target:
        if cur < target:
            end += 1
            if end == n * 2:
                return -1
            cur += que3[end]
        else:
            cur -= que3[start]
            start += 1
        ans += 1
    return ans
 ```
> 이분도 -1 return 조건을 그냥 전체 길이 `end == n*2`로 그냥 넉넉히 주셨다.
