# ES6 함수의 추가 기능

## 메서드

> ES6 사양에서 메서드는 메서드 축약 표현으로 정의된 함수만을 의미한다.

```js
const obj = {
  x: 1,
  foo() {
    console.log('b');
  }, // 메서드
  bar: function () {
    console.log('c');
  }, // 메서드 아님
};
```

**메서드의 특징**

1. 생성자 함수로 사용할 수 없음.
2. 프로토타입 객체가 없음.
3. 내부슬롯 [[HomeObject]]를 갖는다.
   > 자신을 바인딩한 객체를 가리키며, super 키워드로 사용한다.

```js
const a = {
  name: 'ko',
  sayHi() {
    return `hi! ${name}`;
  },
};

const b = {
  __proto__: a,
  sayHi() {
    return `${super.sayHi()}, :)`;
  },
};

console.log(b.sayHi());
```

## 화살표 함수

1. 화살표 함수 내부에서 참조하는 this(상위 스코프의 this)를 lexical this라고 부른다.
2. 화살표 함수 내부에서 arguments는 상위 스코프의 arguments를 참조한다.
