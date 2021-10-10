# Iterable

**Iterable 은 순회가능한 데이터 컬렉션 자료구조**를 만들기 위해 ECMAScript 사양에 정의하여 미리 약속한 규칙이다. 원래는 여러가지 자료구조 형태가, **for 문, for...in 등 자신의 방법대로 순회**할 수 있었으나, 이를 ES6 부터 **for..of 문, 스프레드 문법, 배열 디스트럭처링 할당**등으로 사용할 수 있도록 일원화 했다.

이터레이션 프로토콜에는 아래와 같은 프로토콜이 있다.

## Iterable-Protocol

**Symbol.iterator 를 프로퍼티키로 사용한 메서드를 직접 구현**하거나, 프로토타입 체인을 통해 상속을 받은 **Symbol.iterator 메서드를 호출하면 이터레이터 프로토콜을 준수한 이터레이터를 반환**한다. **Iterable-Protocol 을 준수한 객체를 이터러블**이라한다. 이터러블은 **for...of 문으로 순회할 수 있으며, 스프레드 분법과 배열 디스트럭처링 할당의 대상으로 사용**할 수 있다.

## Iterator-Protocol

이터러블의 Symbol.iterator 메서드를 호출하면 이터레이터 프로토콜을 준수한 이터레이터를 반환한다. 이터레이터는 next 메서드를 소유하며 next 메서드를 호출하면 이터러블을 순회하며 value 와 done 을 갖는 property 를 갖는 이터레이터 Result 객체를 반환한다.

```javascript=
const array = [1,2,3];
const obj = {a: 1, b: 2};

console.log(Symbol.iterator in array); // true
console.log(Symbol.iterator in obj); // false

for(const ele of array) {
  console.log(ele)
}

for(const obj of array) { // 불가능
  console.log(ele)
}
```
