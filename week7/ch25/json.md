# 클래스

> 객체지향 프로그래밍 언어와 매우 흡사한 새로운 객체 생성 메커니즘

> 클래스에 의해 생성된 인스턴스에도 프로토타입의 체인은 동일하게 적용된다. 그러므로 클래스도 프로토타입 기반의 객체 생성 메커니즘

## 클래스와 생성자 함수의 차이

1. new 연산자 없이 호출 시 에러

   > 클래스는 인스턴스를 생성하는 것이 목적이므로 반드시 new 연산자와 함께 호출해야 한다.

2. extends와 super 제공

   > 상속 클래스의 생성자 함수는 일반 클래스와 다르게 부모 클래스의 생성자가 빈 객체를 만들기 때문에 super를 호출하여 this가 될 빈 객체를 만들어야 한다. 즉, super는 this이전에 호출되어야 함

```js
class Car {
  constructor(name) {
    this.name = name;
  }
}
class Truck extends car {
  constructor(name) {
    // 에러 1
    this.wheel = 4;
    super(name);

    // 에러 2
    this.wheel = 4;

    // 정상
    super(name);
    this.wheel = 4;
  }
}
```

3. 클래스는 호이스팅이 발생하지 않는 것처럼 동작한다.

4. 클래스는 strict mode가 암묵적으로 설정된다.

5. 클래스의 constructor, 프로토타입 메서드, 정적 메서드는 [[Enumerable]]이 false. (열거되지 않음)

---

## 클래스 정의

1. 클래스는 함수이기에 표현식으로 정의할 수 있다.

```js
class Person {}
console.log(typeof Person); // function
```

2. 클래스도 호이스팅이 발생한다.

```js
const Person = '';
{
  console.log(Person);
  // Uncaught ReferenceError: Cannot access 'Person' before initialization
  class Person {}
}
```

> let, const와 동일하며, 마찬가지로 TDZ에 빠짐

---

## 메서드

### 프로토타입 메서드

클래스 몸체에서 정의한 메서드는 기본적으로 프로토타입 메서드가 된다.

```js
// 생성자 함수
function Car(name) {
  this.name = name;
}

// 프로토 타입 메서드
Car.prototype.sayHello = function () {
  console.log(`Hi! My name is ${this.name}`);
};

// 클래스
class Car {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    // 프로토타입 메서드
    console.log(`Hi! My name is ${this.name}`);
  }
}
```

### 정적 메서드

> 인스턴스를 생성하지 않아도 호출할 수 있는 메서드

> 정적 메서드는 인스턴스 프로퍼티를 참조하지 않으므로 인스턴스 프로퍼티를 참조해야 할 때는 프로토타입 메서드를 사용한다.

```js
class Car {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    // 프로토타입 메서드
    console.log(`Hi! My name is ${this.name}`);
  }
}
```

#### 클래스의 constructor 메서드와 프로토타입의 constructor 프로퍼티

클래스의 constructor 메서드

- 인스턴스를 생성하고 초기화하기 위한 메서드

프로토타입의 constructor 프로퍼티

- 모든 프로토타입이 가지고 있는 프로퍼티, 생성자 함수를 가리킨다.

#### 모든 선언문은 런타임 이전에 먼저 실행된다.

var, let, const, function, funtion\*, class 키워드를 사용하여 선언된 모든 식별자는 호이스팅된다.
