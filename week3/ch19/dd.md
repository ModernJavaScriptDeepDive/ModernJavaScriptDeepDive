# 프로토타입

## \_\_proto\_\_를 통해 [[prototype]] 내부 슬롯에 접근하는 이유

> 상호 참조에 의해 프로토타입 체인이 생성되는 것을 방지하기 위해서 

## 가급적 \_\_proto\_\_를 직접 사용하진 말자

- 직접 상속을 통해 Object.prototype을 상속받지 않는 객체도 있다. 

```javascript
const obj = Object.create(null)
```

- 따라서 프로토타입의 참조를 취득하고 싶다면 Object.getPrototypeOf를 사용하고,

- 프로토타입을 교체하고 싶다면 Object.setPrototypeOf 메서드를 사용하자 

## 생성자 함수로 생성 vs 리터럴로 생성

```javascript
function foo1() {};

const foo2 = function(){};

const bar = new Function();
```

- 선언문, 표현식으로 평가해서 생성한 함수 객체는 Function 생성자 함수로 만든게 아니다. 하지만 constructor 프로퍼티를 확인하면 Function으로 나와있다?

- 프로토타입이 필요하기에 가상의 생성자 함수를 지정한 것

- new Function(). 생성자 함수로 생성한 함수는 렉시컬 스코프를 만들지 않고 전역 함수처럼 스코프를 생성한다

- 클로저 또한 만들지 않는다

> 프로토타입과 생성자 함수는 단독으로 존재할 수 없고 언제나 쌍으로 존재한다. 

## 추상연산. OrdinaryObjectCreate

- 빈 객체를 생성하고, 
- 전달 받은 프로토타입을 해당 객체의 [[prototype]] 내부 슬롯에 할당한다(필수 인수)
- 전달 받은 프로퍼티 목록들을 해당 객체에 추가한다(선택 인수)
- 완성된 객체를 반환한다.

## instanceof 

> 좌변에는 객체를 가르키는 식별자 / 우변에는 생성자 함수를 가리키는 식별자를 받는다.

즉 좌변의 객체의 프로토타입 체인에 우변의 객체가 있다면 true로 평가된다. 

## 직접 상속

### Object.create

- 생성할 객체의 프로토타입이 될 객체를 첫 번째 매개변수로

### __proto__에 직접 할당

## 프로퍼티 존재 확인

### in

key in object. 프로토타입의 프로퍼티까지 검색

Reflect.has(object, key) 마찬가지로 프토토타입 프로퍼티까지 검색

Object.hasOwnProperty 그 객체 자체의 프로퍼티만 검색 


## 프로퍼티 열거

### for ... in object

- ...에 선언한 변수에 object의 프로퍼티를 하나씩 할당해서 동작하는데, **상속받은 프로토타입의 프로퍼티가지 열거한다.**

- 단 [[Enumerable]]이 false인 프로퍼티는 열거되지 않는다.

> for ... in 문을 객체의 **프로토타입 체인 상에 존재하는 모든 프로퍼티** 중에서 프로퍼티 어트리뷰트 [[Enumerable]]가 true인 것만 열거한다

- 지정한 객체의 프로퍼티만 열거하고 싶다면 hasOwnProperty로 체크해야한다. 

- object.keys/values/entries로 객체 자신의 키/값을 배열로 받아서 배열로 반복을 돌리자

- 따라서 배열의 반복은 for in대신 for, for of, 고차함수 메소드등을 쓰자



