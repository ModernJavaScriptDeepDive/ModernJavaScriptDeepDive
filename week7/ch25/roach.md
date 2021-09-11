# Class

### 클래스와 생성자 함수의 차이

1. 클래스를 new 연산자 없이 호출하면 에러가 발생된다. 하지만 생성자 함수는 new 없이 호출하면 일반 함수로서 호출된다.
2. 클래스는 상속을 지원하는 extend 와 super 를 지원한다.
3. 클래스는 호이스팅이 발생하지 않는 것처럼 동작한다.
4. 클래스 내의 모든 코드에는 암묵적으로 `strict mode` 가 적용된다.
5. 클래스의 constructor, proptotype method, static method 모두 property attribute [[Enumerable]] 의 값이 false 다.

### 클래스 정의

```javascript=
class Person {}
```

일반적이지는 않지만 아래와 같은 방식으로도 정의가 가능하다.

```javascript=
const Person = class {}

const Person = class MyClass {}
```

위와 같은 **표현식 방식이 가능하다는 것은 class 가 값으로 사용가능한 일급 객체**임을 의미한다.

### 인스턴스 생성

클래스는 생성자 함수이며 new 연산자와 함께 호출되어 인스턴스를 생성한다.

```javascript=
class Person {}

const me = new Person();
console.log(me);
```

### 생성자

```javascript=
class Person {

    constructor(name) {
        this.name = name;
    }

}
```

위와 같이 **constructor 에 class 내에서 사용할 property 를 기술**한다.
인스턴스 property 는 반드시 constructor 내부에 기술해야 하낟.
그래야만 클래스가 암묵적으로 생성한 빈 객체, 즉 인스턴스에 프로퍼티가 추가되어 인스턴스가 초기화된다.

### 정적 메서드와 프로토타입 메서드의 차이

1. 정적 메서드와 프로토타입 메서드는 자신이 속해있는 프로토타입 체인이 다르다.
2. 정적 메서드는 클래스로 호출하고, 프로토 타입메서드는 인스턴스로 호출한다.
3. 정적 메서드는 인스턴스 프로퍼티를 참조할 수 없지만 프로토타입 메서드는 인스턴스 프로퍼티를 참조할 수 있다.

```javascript=
class Util {

    constructor(width, height) {
        this.width = width;
        this.height = height;
    }

    inner_area() {
        return this.witdh * this.height;
    }

    static area(width, height) {
        return width * height;
    }

}
```

위와 같이 static 메소드는 내부 property 를 사용할 수 없다.

### 인스턴스 생성 과정

1. 인스턴스 생성과 this binding

new 연산자와 함께 클래스를 호추랗면 constructor 의 내부 코드가 실행되기에 앞서 암묵적으로 빈 객체가 생성된다. 이때 클래스가 생성한 인스턴스의 프로토타입으로 클래스의 property 가 가르키는 객체가 생성된다.

2. 인스턴스 초기화

constructor 의 내부 코드에 실행되어 this에 바인딩 되어 있는 인스턴스를 초기화 한다.

3. 클래스의 모든 처리가 끝나면 인스턴스를 반환한다.

### 접근자 메소드

```javascript=
class Person {

    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    get fullName() {
        return this.fullName;
    }

    set fullName(fullName) {
        return this.fullName = fullName;
    }

}
```

### super keyword

super 를 호출하면 constructor (super-constructor) 를 호출한다.
