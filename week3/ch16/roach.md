# 프로퍼티 어트리뷰트와 프로퍼티 디스크립터 객체

자바스크립트 엔진은 프로퍼티를 생성할 때 프로퍼티의 상태를 나타내는 프로퍼티 어트리뷰트를 기본값으로 자동 정의한다. 프로퍼티의 상태란 프로퍼티의 값, 값의 갱신 가능 여부, 열거 가능여부, 재정의 가능 여부를 말한다.

프로퍼티 어트리뷰트는 자바스크립트 엔진이 관리하는 내부 상태 값인 내부슬롯, [[Value]], [[Writable]], [[Enumerable]], [[Configurable]] 이다.

- [[Value]] : 프로퍼티 키를 통해 **프로퍼티 값을 변경하면, [[Value]] 에 값을 재할당** 한다. 이때 프로퍼티가 없으면, 프로퍼티를 동적 생성하고 생성된 프로퍼티의 [[Value]] 에 값을 저장한다.

- [[Writable]] : 프로퍼티 값의 **변경 가능 여부를 나타내며 Boolean 값**을 갖는다. => 그럼 **readonly 는 이거를 false 를 주나보다 ㅋㅋ**

- [[Enumerable]] : 프로퍼티의 열거 가능 여부를 나타내며 불리언 값을 갖는다.

- [[Configurable]] : 프로퍼티 재정의 가능 여부를 나타내며 Boolean 값을 갖는다. => 이거 써보면 DDD 에서 요구하는 최종 객체.. 이런거 해볼수 있지 않을까?

```javascript
const person = {};

Object.defineProperty(person, "firstName", {
  value: "roach",
  writable: false,
  enumerable: true,
  configuralbe: false,
});

console.log(person); // roach

person.firstName = "zzz";

console.log(person); // roach
```

## 객체 변경 방지

- 객체는 변경 가능한 값이므로 재할당없이 직접 변경이 가능하다.

Object.preventExtensions => 프로퍼티 추가만 불가

Object.seal => 값 읽기 쓰기만 가능

Object.freeze => 프로퍼티 값 읽기만 가능
