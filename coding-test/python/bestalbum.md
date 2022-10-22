
#### 🥏 Programmers
# [베스트 앨범](https://school.programmers.co.kr/learn/courses/30/lessons/42579?language=python3)
`level 3` , `hash`

### 문제 설명

> 스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다. <br>
속한 노래가 많이 재생된 장르를 먼저 수록합니다. <br>
장르 내에서 많이 재생된 노래를 먼저 수록합니다. <br>
장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다. <br>
노래의 장르를 나타내는 문자열 배열 genres와 노래별 재생 횟수를 나타내는 정수 배열 plays가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요. <br>
> 


#### Constraints:
- genres[i]는 고유번호가 i인 노래의 장르입니다.
- plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
- genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
- 장르 종류는 100개 미만입니다.
- 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
- 모든 장르는 재생된 횟수가 다릅니다.

<br><br>

## 👩🏻‍💻 문제 풀이

##### 🙎🏻‍♂️ 작성자 : 김윤겸([@yoongyum](github.com/yoongyum))


~~~python
from collections import defaultdict, deque


def solution(genres, plays):
    answer = []
    gen = defaultdict(int)  # 속한 노래가 많이 재생된 장르를 기준으로 정렬하기 위해 선언
    gen2 = defaultdict(deque)  # 해당 장르별로 재생된 횟수를 기준으로 정렬하기 위해 선언
    for i, (genre, play) in enumerate(zip(genres, plays)):
        gen[genre] += play
        gen2[genre].append((i, play))

    gen = sorted(gen.items(), key=lambda x: x[1], reverse=True)
    for key, val in gen:  # O(N)
        genre = sorted(gen2[key], key=lambda x: x[1], reverse=True)[:2]  # O(NlogN) 정렬 후 크기가 최대 2개의 리스트로 반환
        for tuples in genre:
            answer.append(tuples[0])
    return answer
~~~

## 해설 
1. 장르마다 가장 많이 재생된 기준으로 정렬하기 위해 해쉬맵을 생성, 누적으로 더한다.
2. 장르 내에서 재생횟수를 기준으로 정렬하기 위해 해쉬를 생성, 저장할 때 인덱스와 함께 저장한다.
3. 조건에 의해 정렬된 장르 순으로 반복문을 실행한다.
4. 장르내에 재생수만큼 정렬한 뒤 크기가 2를 넘지않는 리스트로 반환한다.
<br>

소요시간 50분

