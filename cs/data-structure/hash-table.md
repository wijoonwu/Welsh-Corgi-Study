# ❓ What Is Hash Table

> **Hash Tables** 는 `Key-Value System` 을 이용해 자료를 정리한다. `Key-Value System`의 대표적인 예시로는 사전이 있다. 사전의 경우에는 단어가 `Key`, 단어의 뜻과 설명이 `Value`가 된다.

## ⌛️ 시간 복잡도
**Array**와 비교를 통해 <u>레스토랑 메뉴</u>를 예시로, **Hash Table** 의 시간 복잡도를 알아보자.

### Array

```js
menu = [
    { name: "coffee", price: 10 },
    ...
    ...
    ...
    { name: "burger", price: 15 }

];
```

`burger`의 가격을 알고 싶다면 **선형 검색**(linear search)을 통해 배열의 시작부터 끝까지 검색해야하는데, 일일히 하나하나 찾는 방식은 시간이 오래 소요된다.

### Hash Table


```js
menu = {
    coffee: 10,
    ...
    ...
    ...
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

그런데 잠깐, 해쉬 테이블에 Array 구조가 있다면서 어떻게 Hash Table이 Array 보다 훨씬 빠른 것일까? 바로 Hash Function 덕분이다.

## Hash Function
 Hash Function은 가 저장하고 싶은 Key를 숫자로 바꿔준다. 그리고 그 숫자는 Index가 되며, 해당 Index에 Value 가 저장된다.


# 참고
- [개발자라면 꼭 알아야할 Hash Table 의 모든 것! by 노마드코더](https://www.youtube.com/watch?v=HraOg7W3VAM)
