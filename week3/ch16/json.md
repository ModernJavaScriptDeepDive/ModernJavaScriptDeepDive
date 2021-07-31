# 프로퍼티 어트리뷰트

## 내부 슬롯, 내부 메서드

> 자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 ECMAScript 사양에서 사용하는 의사 프로퍼티와 의사 메서드
>
> - 모자스 :lizard:

원친적으로 개발자가 직접 접근하거나 호출할 수는 없지만 간접적으로 접근할 수 있는 일부 슬롯과 메서드가 있음.

대표적인게 <code>**proto**</code>로 접근 가능한 <code>\[\[Prototype\]\]</code>

## 프로퍼티 어트리뷰트와 프로퍼티 디스크립터 객체

> 자바스크립트 엔진은 프로퍼티를 생성할 때, 프로퍼티의 상태를 나타내는 프로퍼티 어트리뷰트를 기본값으로 자동 정의한다.
>
> - 모자스 :lizard:

**프로퍼티의 상태**

1. <code>\[\[Value\]\]</code> : 프로퍼티의 값
2. <code>\[\[Writable\]\]</code> : 값의 갱신 가능 여부
3. <code>\[\[Enumerable\]\]</code> : 열거 가능 여부
4. <code>\[\[Configurable\]\]</code> : 재정의 가능 여부

**프로퍼티 어트리뷰트**

자바스크립트 엔진이 관리하는 내부 상태 값인 위의 4개를 의미함.  
내부 슬롯이기에 직접적인 접근은 불가능하지만 Object.getOwnPropertyDescriptor 메서드를 사용하여 간접적으로 확인할 수 있다.

```js
const person = {
  name: 'wooluck',
};

console.log(Object.getOwnPropertyDescriptor(person, 'name'));
// {value: "wooluck", writable: true, enumerable: true, configurable: true}
```

새로운 프로퍼티를 추가할 때, 프로퍼티 어트리뷰트를 명시적으로 정의할 수 있다.
<code>Object.defineProperty</code>

> 명시적으로 정의할 경우 프로퍼티의 어트리뷰트는 기본값이 false, undefined

```js
wooluck = { price: '싯가' };
Object.getOwnPropertyDescriptor(wooluck, 'price');
Object.defineProperty(wooluck, 'age', {
  value: 1, // 기본값 undefined
  writable: true, // 기본값 false
  enumerable: true, // 기본값 false
  configurable: true, // 기본값 false
  get: fn(), // 기본값 undefined
  set: fn(), // 기본값 undefined
});

// ES8에서 도입된 getOwnPropertyDescriptors는 모든 프로퍼티의 어트리뷰트를 제공함.
Object.getOwnPropertyDescriptors(w);
// age: {value: 1, writable: true, enumerable: true, configurable: true}
// price: {value: '싯가', writable: true, enumerable: true, configurable: true}
```

**데이터 프로퍼티와 접근자 프로퍼티**

- 데이터 프로퍼티

> 키와 값으로 구성된 일반적인 프로퍼티.
>
> - 모자스 :lizard:

- 접근자 프로퍼티

> 자체적으로는 값이 없다.  
> 다른 데이터 프로퍼티의 값을 일거나 저장할 때 호출되는 접근자 함수로 구성되어 있는 프로퍼티
>
> 접근자 함수를 getter/setter라고 부르기도 한다.
>
> - 모자스 :lizard:
