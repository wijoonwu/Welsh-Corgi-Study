
#### π₯ Programmers
# [λ ν ν© κ°κ² λ§λ€κΈ°](https://school.programmers.co.kr/learn/courses/30/lessons/118667)
`level 2` , `kakao`, `queue`

### λ¬Έμ  μ€λͺ

> λ¬Έμ λ λλ¬΄ κΈΈμ΄μ μλ΅. μ λ§ν¬μμ μ°Έκ³  <br>
> λ¬Έμ  μ λͺ©μ΄ λ¬Έμ μ


#### Constraints:
- 1 β€ queue1μ κΈΈμ΄ = queue2μ κΈΈμ΄ β€ 300,000
- 1 β€ queue1μ μμ, queue2μ μμ β€ 10^9 

μ£Όμ: μΈμ΄μ λ°λΌ ν© κ³μ° κ³Όμ  μ€ μ°μ  μ€λ²νλ‘μ° λ°μ κ°λ₯μ±μ΄ μμΌλ―λ‘ long type κ³ λ €κ° νμν©λλ€.

<br><br>

## π©π»βπ» λ¬Έμ  νμ΄

##### ππ»ββοΈ μμ±μ : κΉμ€κ²Έ([@yoongyum](github.com/yoongyum))


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

## ν΄μ€ 
0. λμ ν©μ μ€κ°μ κ΅¬νλ€. `total`
1. λ νμ ν©μ΄ νμμ΄λ©΄ λ°λ‘ μ’λ£ 
2. μκ° ν¨μ¨μ±μ μν΄ `deque`λ‘ λ³κ²½
3. μ΄κΈ°μ λ νμ ν©μ λ―Έλ¦¬ κ΅¬ν΄λλλ€. `leftSum`, `rightSum`
  - πμ΄μ  : `while`λ¬Έ μμμ `sum` ν¨μλ₯Ό μ¬μ©νλ©΄ μκ°μ΄κ³Όλ¨
4. `while`λ¬Έ μ€ν 
5. νμͺ½ κ°μ΄ `total` κ°κ³Ό κ°μμ§λ©΄ μ’λ£
6. λ μ€ ν©μ΄ ν° μͺ½μμ λΉΌκ³  μμ μͺ½μ λν΄μ€λ€.
7. μλ¬΄λ¦¬ ν΄λ λͺ»κ΅¬νλ κ²½μ° `-1`μ λ°ννλ€.
  - λͺ»κ΅¬νλ μ‘°κ±΄μ  `if answer > limit1 + limit2 + 2:`λ‘ μ§κΈ΄ νλλ° μλλμ§ λͺ¨λ₯΄κ² λ€.

<br>

### π‘ μλ‘ μκ²λ μ 
λ€λ₯Έ λΆμ μ½λμΈλ° 

νλ₯Ό νλλ‘ ν©μ³μ νλλ§ μ¨μ

`start`, `end` ν¬ ν¬μΈν°λ‘ νΈμ κ±° κ°λ€. 

#### π λ€λ₯Έμ¬λ νμ΄ μ½λ
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
> μ΄λΆλ -1 return μ‘°κ±΄μ κ·Έλ₯ μ μ²΄ κΈΈμ΄ `end == n*2`λ‘ κ·Έλ₯ λλν μ£Όμ¨λ€.
