
# 🥏 Programmers
## 신고 결과 받기
- https://school.programmers.co.kr/learn/courses/30/lessons/92334?language=python3

### 문제 설명

> 신입사원 무지는 게시판 불량 이용자를 신고하고 처리 결과를 메일로 발송하는 시스템을 개발하려 합니다. <br>
무지가 개발하려는 시스템은 다음과 같습니다. <br>
각 유저는 한 번에 한 명의 유저를 신고할 수 있습니다. <br>
신고 횟수에 제한은 없습니다. 서로 다른 유저를 계속해서 신고할 수 있습니다. <br>
한 유저를 여러 번 신고할 수도 있지만, 동일한 유저에 대한 신고 횟수는 1회로 처리됩니다. <br>
k번 이상 신고된 유저는 게시판 이용이 정지되며, 해당 유저를 신고한 모든 유저에게 정지 사실을 메일로 발송합니다. <br>
유저가 신고한 모든 내용을 취합하여 마지막에 한꺼번에 게시판 이용 정지를 시키면서 정지 메일을 발송합니다. <br>
다음은 전체 유저 목록이 ["muzi", "frodo", "apeach", "neo"]이고, k = 2(즉, 2번 이상 신고당하면 이용 정지)인 경우의 예시입니다. <br>


#### Constraints:
- 2 ≤ id_list의 길이 ≤ 1,000
- 1 ≤ id_list의 원소 길이 ≤ 10
- id_list의 원소는 이용자의 id를 나타내는 문자열이며 알파벳 소문자로만 이루어져 있습니다.
- id_list에는 같은 아이디가 중복해서 들어있지 않습니다.
- 1 ≤ report의 길이 ≤ 200,000
- 3 ≤ report의 원소 길이 ≤ 21
- report의 원소는 "이용자id 신고한id"형태의 문자열입니다.
- 예를 들어 "muzi frodo"의 경우 "muzi"가 "frodo"를 신고했다는 의미입니다.
- id는 알파벳 소문자로만 이루어져 있습니다.
- 이용자id와 신고한id는 공백(스페이스)하나로 구분되어 있습니다.
- 자기 자신을 신고하는 경우는 없습니다.
- 1 ≤ k ≤ 200, k는 자연수입니다.
- return 하는 배열은 id_list에 담긴 id 순서대로 각 유저가 받은 결과 메일 수를 담으면 됩니다.

<br><br>

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


~~~python
from collections import defaultdict
def solution(id_list, report, k):
    id = defaultdict(set)
    ban = defaultdict(int)
    #신고한 리스트 해쉬셋으로 저장 - 중복 신고 불가
    for re in report:
        key, val = re.split(' ')
        id[key].add(val)
    #유저별로 신고된 횟수 처리
    for user in id_list:
        for target in id[user]:
            ban[target] += 1
    #유저마다 정지시킨 횟수 리턴
    answer = []
    for user in id_list:
        cnt = 0
        for target in id[user]:
            if ban[target] >= k:
                cnt += 1 
        answer.append(cnt)
    return answer
~~~
### 💬 코드 해설
>

### 💡 새로 알게된 점
> report를 set으로 만들어서 처리하는 게 더 좋을 듯 하다.
