# Symbol?

JavaScript 에서 **Symbol** 이란, **다른값과 중복되지 않는 유일무이한 값**이다. 따라서 주로 이름 **충돌이 없는 유일한 Property 키를 만들기 위해 사용**한다. 여담으로 Ruby 든 다른 언어에도 모두 Symbol 이 존재하는데, 사용용도는 항상 비슷하게 **유일한 프로퍼티키를 만들기 위해서 사용**한다.

## 심벌 값의 생성

```javascript=
const mySymbol = Symbol();
console.log(type of mySymbol); // symbol

console.log(mySymbol); // Symbol();
```

Symbol() 이라는 메소드를 얼핏 보면 새롭게 인스턴스를 만드는 것 같지만, 심벌 값은 **변경 불가능한 원시 값**이다. 심벌값도 암묵적으로 **Wrapper Object 를 생성**한다.

```javascript=
const mySymbol1 = Symbol('mySymbol');
const mySymbol2 = Symbol('mySymbol');

console.log(mySymbol1 === mySymbol2) // false
```

## Symbol.for / Symbol.keyFor 메서드

인수로 전달받은 문자열을 통해서 Symbol 값을 찾는다.
Symbol 값을 찾기 위해서는 아래와 같은 형태로 입력해주면 된다.

```javascript=
Symbol.for('roach') // create if not exist
```

이 방식은 해당 문자열로 구성된 Symbol 이 존재하지 않으면, 새로운 심벌값을 생성해서 반환해준다.

```javascript=
Symbol.keyFor('roach');
```

위의 방식을 이용하면 전역 심벌 레지스트리에 저장된 심벌 값의 키를 추출할 수 있다.

## Enum

```javascript=
const Direction = Object.freeze({
    UP: Symbol('UP'),
    DOWN: Symbol('DOWN'),
    LEFT: Symbol('LEFT'),
    RIGHT: Symbol('RIGHT'),
});
```
