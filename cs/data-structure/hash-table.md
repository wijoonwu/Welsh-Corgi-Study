# ❓ What Is Hash Table

> **Hash Tables** 는 `Key-Value System` 을 이용해 자료를 정리한다. `Key-Value System`의 대표적인 예시로는 사전이 있다. 사전의 경우에는 단어가 `Key`, 단어의 뜻과 설명이 `Value`가 된다.

## ⌛️ 시간 복잡도
**Array**와 비교를 통해 <u>레스토랑 메뉴</u>를 예시로, **Hash Table** 의 시간 복잡도를 알아보자.

### Array

```js
menu = [
    { name: "coffee", price: 10 },
    ...,
    ...,
    ...,
    { name: "burger", price: 15 }

];
```

`burger`의 가격을 알고 싶다면 **선형 검색**(linear search)을 통해 배열의 시작부터 끝까지 검색해야하는데, 일일히 하나하나 찾는 방식은 시간이 오래 소요된다.

### Hash Table


```js
menu = {
    coffee: 10,
    ...,
    ...,
    ...,
    burger: 15
};
```

같은 메뉴지만  **Hash Table**로 정리하면 `burger` 는 `Key`, 가격은 `Value`가 된다.
어떤 메뉴의 값을 찾더라도 **Hash Table**은 딱 1개의 단계만 소요 되는 것이다.

**Array**의 시간 복잡도는 `O(N)`인 반면, **Hash Table**은 아이템을 추가할 때도, 삭제할 때도 `O(1)`이다. **Array**랑 비교하면 엄청나게 빠르다.


# 🕵️‍♀️ How It Works
작동 원리를 알아보기에 앞서, **Hash Table**의 `Hash`는 뭘까?
**Hash Table** 에는 **Array** 구조가 있고, 모든 **Hash Table**의 값들은 **Array** 구조 안에 있다. 그리고 Array에서 아이템에 접근하기 위해서는 Index 번호를 알아야한다.

|Index|Value|
|:---:|:---:|
|0|value_1|
|1|value_2|
|2|value_3|

그런데 잠깐, **Hash Table** 에 **Array** 구조가 있다면서 어떻게 **Hash Table**이 **Array** 보다 훨씬 빠른 것일까? 바로 **Hash Function** 덕분이다.

## Hash Function
<img src="https://github.com/wijoonwu/Welsh-Corgi-Study/blob/main/static/img/hash-function.png?raw=true">

 **Hash Function**은 가 저장하고 싶은 `Key`를 숫자로 바꿔준다. 그리고 그 숫자는 `index`가 되며, 해당 `index`에 `Value` 가 저장된다.

무슨 말인지 헷갈릴 수 있으니 다시 메뉴판을 예로 들어서 설명하겠다.
만약 `pizza` 의 가격을 저장할 때는 아래와 같다. 

1. `pizza`의 알파벳 글자 수를 센다.
2. `pizza`의 글자수 5 -> `index` 5번에 저장한다.
3. `index` 5의 value에 10,000원을 저장한다.

나중에 pizza 가격이 궁금하다면 아래와 같은 방법으로 찾을 수 있다.
1. **Hash Function**에 pizza라는 key를 준다.
2. **Hash Function**은 숫자 5를 알려준다.
3. `index` 5의 Value로 가격을 찾는다.

### Collision(해쉬 충돌)
그런데 **Hash Function**에는 한가지 문제점이 있다. 각기 다른 `Key`에 대하여 **Hash Function** 이 동일한 숫자를 준 경우 말이다.

예를 들어 `cake`를 해쉬 테이블에 넣었다. **Hash Function**은 `index` 4를 줬고, `value`에는 5,000원이 저장됐다. 그런데 나중에 `taco`도 넣으려고 하니 **Hash Function**이 또 `index` 4를 줬고, 해당 자리에는 이미 `cake`가 있다.

<img src="https://github.com/wijoonwu/Welsh-Corgi-Study/blob/main/static/img/collision.png?raw=true">

여러가지 대처법 중 한가지는 바로 `index` 4의 공간에 또 다른 배열을 넣는 것이다.
그리고 해당 배열에 2개의 `cake`와 `taco`. 2개의 쌍을 저장한다.
이제 우리 **Hash Table** 에서 `cake`의 가격을 찾고자 한다면
`cake` 라는 key를 해시 함수에 넣고 4라는 숫자를 받아서
리스트 4로 이동한 뒤 `cake`의 가격을 찾을 때까지 선형 검색을 하면 되는 것이다.
이런 이유 때문에 해쉬 테이블의 시간복잡도가 언제나 `O(1)` 인 것은 아니지만
그래도, 여전히 우리는 전반적인 시나리오 중심으로 판단해야하기 때문에
**Hash Table**의 시간 복잡도는 상수시간(`O(1)`)이라고 볼 수 있다.


# Reference
- [개발자라면 꼭 알아야할 Hash Table 의 모든 것! by 노마드코더](https://www.youtube.com/watch?v=HraOg7W3VAM)
