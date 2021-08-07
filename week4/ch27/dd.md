# 배열

> 자바스크립트의 배열은 사실 배열이 아니다. 일반적인 배열의 동작을 흉내 낸 특수한 **객체**다

- 배열의 각 요소가 동일한 메모리 공간을 가지고 있지 않다

- 연속적으로 이어져있지 않을 수도 있다. 이를 희소 배열(sparse array)이라 한다

## 일반적인 배열과의 차이

- 일반 배열은 인덱스로 요소에 빠르게 접근 가능하지만, 자바스크립트 배열은 객체이기에 상대적으로 느리다

- 하지만 특정 요소 검색, 요소 삽입/삭제/수정는 일반 배열보다 빠르다.

## 자바스크립트 배열 / 객체 

- 배열에 최적화된 객체 이기에 요소 삽입의 경우 약 2배정도 차이난다(배열이 더 빠름)

## 희소배열

> length와 배열 요소의 개수가 반드시 일치하는 건 아니다. 최소 1더 크거나, 그 이상 클 수도 있다.

## 메소드

### Array.push

- `array.push(()`를 사용하는 것보다 `array[array.length] = value`가 더 빠르다.

### Array.fill

- 해당 배열 요소를 첫번째 인자로 치환한다

- 두 번째, 세 번째로 어디부터 어디까지 치환할지 정할 수 있음

### Array.includes

- 배열에 그 값이 있는지 없는지, 두 번째 요소로 검색 시작점을 지정할 수 있음. -의 경우 length-n부터 검색 

### Array.flat

- 인수로 전달한 깊이만큼 재귀적으로 **배열을 평탄화**한다

- 배열안의 배열 요소를 밖으로 꺼낼 때 사용. 근데 쓸일 있는지??





