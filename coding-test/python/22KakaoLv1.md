
# π₯ Programmers
## μ κ³  κ²°κ³Ό λ°κΈ°
- https://school.programmers.co.kr/learn/courses/30/lessons/92334?language=python3

### λ¬Έμ  μ€λͺ

> μ μμ¬μ λ¬΄μ§λ κ²μν λΆλ μ΄μ©μλ₯Ό μ κ³ νκ³  μ²λ¦¬ κ²°κ³Όλ₯Ό λ©μΌλ‘ λ°μ‘νλ μμ€νμ κ°λ°νλ € ν©λλ€. <br>
λ¬΄μ§κ° κ°λ°νλ €λ μμ€νμ λ€μκ³Ό κ°μ΅λλ€. <br>
κ° μ μ λ ν λ²μ ν λͺμ μ μ λ₯Ό μ κ³ ν  μ μμ΅λλ€. <br>
μ κ³  νμμ μ νμ μμ΅λλ€. μλ‘ λ€λ₯Έ μ μ λ₯Ό κ³μν΄μ μ κ³ ν  μ μμ΅λλ€. <br>
ν μ μ λ₯Ό μ¬λ¬ λ² μ κ³ ν  μλ μμ§λ§, λμΌν μ μ μ λν μ κ³  νμλ 1νλ‘ μ²λ¦¬λ©λλ€. <br>
kλ² μ΄μ μ κ³ λ μ μ λ κ²μν μ΄μ©μ΄ μ μ§λλ©°, ν΄λΉ μ μ λ₯Ό μ κ³ ν λͺ¨λ  μ μ μκ² μ μ§ μ¬μ€μ λ©μΌλ‘ λ°μ‘ν©λλ€. <br>
μ μ κ° μ κ³ ν λͺ¨λ  λ΄μ©μ μ·¨ν©νμ¬ λ§μ§λ§μ νκΊΌλ²μ κ²μν μ΄μ© μ μ§λ₯Ό μν€λ©΄μ μ μ§ λ©μΌμ λ°μ‘ν©λλ€. <br>
λ€μμ μ μ²΄ μ μ  λͺ©λ‘μ΄ ["muzi", "frodo", "apeach", "neo"]μ΄κ³ , k = 2(μ¦, 2λ² μ΄μ μ κ³ λΉνλ©΄ μ΄μ© μ μ§)μΈ κ²½μ°μ μμμλλ€. <br>


#### Constraints:
- 2 β€ id_listμ κΈΈμ΄ β€ 1,000
- 1 β€ id_listμ μμ κΈΈμ΄ β€ 10
- id_listμ μμλ μ΄μ©μμ idλ₯Ό λνλ΄λ λ¬Έμμ΄μ΄λ©° μνλ²³ μλ¬Έμλ‘λ§ μ΄λ£¨μ΄μ Έ μμ΅λλ€.
- id_listμλ κ°μ μμ΄λκ° μ€λ³΅ν΄μ λ€μ΄μμ§ μμ΅λλ€.
- 1 β€ reportμ κΈΈμ΄ β€ 200,000
- 3 β€ reportμ μμ κΈΈμ΄ β€ 21
- reportμ μμλ "μ΄μ©μid μ κ³ νid"ννμ λ¬Έμμ΄μλλ€.
- μλ₯Ό λ€μ΄ "muzi frodo"μ κ²½μ° "muzi"κ° "frodo"λ₯Ό μ κ³ νλ€λ μλ―Έμλλ€.
- idλ μνλ²³ μλ¬Έμλ‘λ§ μ΄λ£¨μ΄μ Έ μμ΅λλ€.
- μ΄μ©μidμ μ κ³ νidλ κ³΅λ°±(μ€νμ΄μ€)νλλ‘ κ΅¬λΆλμ΄ μμ΅λλ€.
- μκΈ° μμ μ μ κ³ νλ κ²½μ°λ μμ΅λλ€.
- 1 β€ k β€ 200, kλ μμ°μμλλ€.
- return νλ λ°°μ΄μ id_listμ λ΄κΈ΄ id μμλλ‘ κ° μ μ κ° λ°μ κ²°κ³Ό λ©μΌ μλ₯Ό λ΄μΌλ©΄ λ©λλ€.

<br><br>

## π©π»βπ» λ¬Έμ  νμ΄

##### ππ»ββοΈ μμ±μ : κΉμ€κ²Έ([@yoongyum](github.com/yoongyum))


~~~python
from collections import defaultdict
def solution(id_list, report, k):
    id = defaultdict(set)
    ban = defaultdict(int)
    #μ κ³ ν λ¦¬μ€νΈ ν΄μ¬μμΌλ‘ μ μ₯ - μ€λ³΅ μ κ³  λΆκ°
    for re in report:
        key, val = re.split(' ')
        id[key].add(val)
    #μ μ λ³λ‘ μ κ³ λ νμ μ²λ¦¬
    for user in id_list:
        for target in id[user]:
            ban[target] += 1
    #μ μ λ§λ€ μ μ§μν¨ νμ λ¦¬ν΄
    answer = []
    for user in id_list:
        cnt = 0
        for target in id[user]:
            if ban[target] >= k:
                cnt += 1 
        answer.append(cnt)
    return answer
~~~


### π‘ μλ‘ μκ²λ μ 
#### λ€λ₯Έμ¬λ νμ΄ μ½λ
```py
def solution(id_list, report, k):
    answer = [0] * len(id_list)    
    reports = {x : 0 for x in id_list}

    for r in set(report):
        reports[r.split()[1]] += 1

    for r in set(report):
        if reports[r.split()[1]] >= k:
            answer[id_list.index(r.split()[0])] += 1

    return answer
 ```
> reportλ₯Ό setμΌλ‘ λ§λ€μ΄μ μ²λ¦¬νλ κ² λ μ’μ λ― νλ€.
