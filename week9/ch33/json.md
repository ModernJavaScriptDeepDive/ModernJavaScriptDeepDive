# 7번째 데이터 타입 Symbol

> 주로 이름의 충돌 위험이 없는 유일한 프로퍼티 키를 만들기 위해 사용

- Symbol 함수를 호출하여 생성, 리터럴 불가
- Symbol 값은 자바스크립트 엔진이 관리하는 **전역 Symbol 레지스트리**에서 관리한다.
- Symbol 값을 프로퍼티 키로 하면 for ... in 문이나 Object,keys 등으로 탐색할 수 없다!

```js
// Symbol에 전달한 인자 값은 디버깅에 사용되며, Symbol 값 생성에 영향을 주지 않는다.
const symbol = Symbol('여기는 설명이에요.');
symbol.description; // '여기는 설명이에요.'
```

## Symbol.for / Symbol.keyFor 메서드

### Symbol.for

- 인수로 전달받은 문자열과 키가 일치하는 Symbol 값을 검색한다.

```js
const symbolA = Symbol.for('배고픔');
const symbolB = Symbol.for('배고픔');
symbolA === symbolB; // true
```

### Symbol.keyFor

- 인수로 전달받은 Symbol의 키 값을 추출한다.

```js
const symbol = Symbol.for('1');
Symbol.keyFor(symbol); // '1'
```
