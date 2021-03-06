# 클래스

> 새로운 객체 생성 메커니즘

- 자바스크립트에서 클래도 결국은 함수이다
- 단 생성자 함수와는 다르다. 더 엄격하고, 생성자 함수에서는 제공하지 않는 기능도 있다.

- 반드시 new와 함께 호출해야 함
- extends/super 키워드 제공
- 호이스팅이 발생하지 않는 것 처럼 동작
- 암묵적으로 strict mode
- constructor / 프로토타입 메서드 / 정적 메서드 모두 [[Enumerable]]이 false

## 호이스팅

- 클래스 선언문은 함수 선언문처럼 소스평가 과정, 즉 런타임 이전에 먼저 평가된다.

- 평가되어 생성된 함수 객체는 constructor

## 메서드

- constructor도 메서드다! 인스턴스를 생성하고, 초기화하는.

- this를 사용하지 않는 메서드는 정적 메서드로 정의하는 것이 좋다.

- 정적(static) 메서드는 해당 클래스 함수 객체에, 일반 메서드는 클래스 함수 객체의 .prototype 객체에 바인딩 된다.

- 정적 메서드는 **인스턴스로 호출할 수 없다.** 클래스는 인스턴스의 **프로토타입 체인 상에 존재하지 않기 때문이다**

## 클래스의 인스턴스 생성 과정

1. 빈 객체(인스턴스)를 생성한다

2. 이 객체의 프로토타입으로 class의 prototype 프로퍼티가 가르키는 객체를 설정한다

3. 이 객체를 this에 바인딩한다.

4. constructor 내부 코드를 실행해서 this에 바인딩 인스턴스를 초기화한다.

5. 인스턴스를 반환한다

## private

js에서는 아직까지 private를 공식지원하고 있지 않지만(#을 사용하는 방식이 stage 3에 등록되어있고, Node와 크롬은 이미 지원 중이다. ) typescript에서는 지원한다.

단, typescript도 컴파일된 js코드를 보면 은닉화가 되어있지 않다. 즉 **컴파일 과정에서만 은닉화로써 취급한다**

자세한 내용은 [여기](https://ooeunz.tistory.com/105)를 참고하자

## 상속

- extends로 **생성자 함수도 상속 받을 수 있다**

- 즉 [[Construct]] 내부 메서드를 갖는 함수 객체로 평가될 수 있는 모든 표현식이면 상속 가능하다

- 동적으로 상속 대상을 정할 수도 있다

```
class Sample extends (isA ? A : B)
```

## super

- super는 호출/참조가 둘 다 가능한 특수한 키워드다

- 호출하면 super class의 constructor를 호출한다

- 참조하면 super class의 메서드를 호출할 수 있다.

## [[ConstructorKind]]

- 현재 클래스가 상속을 받는 객체인지, 아닌지 구분하는 내부 슬롯

- 다른 클래스를 상속 받지 않는다면, 혹은 생성자 함수라면 "base"이고

- 상속 받는 클래스라면 "derived"이다.

## 수퍼 클래스를 상속 받는 (서브)클래스로 인스턴스를 생성하는 과정

1. 서브 클래스는 빈 객체(인스턴스)를 직접 생성하지 않고, **수퍼 클래스에게 생성을 위임한다.** 그렇기에 서브 클래스의 constructor에서 super를 반드시 호출해야한다

2. 생성된 인스턴스는 **수퍼 클래스의 constructor 내부의 this와 바인딩된다**

- 단, 해당 인스턴스의 **프로토타입**은 수퍼 클래스의 prototype가 가르키는 객체가 아닌 new로 호출한 **서브 클래스의 prototype이 가르키는 객체가 된다**

3. **수퍼 클래스**의 constructor 내부 코드를 실행해서 this에 바인딩 인스턴스를 초기화한다.

4. super의 호출이 종료되면서 인스턴스를 반환하고, 이 인스턴스가 서브 클래스의 this에 바인딩된다.

5. **서브 클래스**의 constructor 내부 코드를 실행해서 this에 바인딩 인스턴스를 초기화한다.

6. 인스턴스를 반환한다
