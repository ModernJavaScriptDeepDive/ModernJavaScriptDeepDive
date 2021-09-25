# ES6 함수의 추가 기능

ES6 이전의 함수들은 함수 사용 목적에 따라 명확히 구분되지 않았음.

**일반 함수로도 호출이 가능했고, 생성자 함수로도 호출이 가능**했음.

이게 문제가 됬던이유는 `[[Call]]` 과 `[[Construct]]` 를 공부했을때 배운것은 인스턴스를 생성할 수 있는 함수 객체는 constructor, 인스턴스를 생성 할수 없는 함수 객체는 non-constructor 인데 ES6 이전의 함수들은 아래와 같은 구분이 되지 않는 특성때문에 아래와 같은 로직이 가능하다.

```javascript=
var person = {
    age: 99,
    myAge: function() { return this.age }
}

var bar = person.myAge;

console.log(bar()); // undefined
```

위와 같은 형태가 가능하다. 물론 undefined 이지만, **위와 같은 형태가 문법적으로 가능하다는게 말이 안된다. 이는 성능상의 문제도 있는데 즉 myAge() 자체가 constructor 처럼 쓰일 수 있다는 것은 property 를 가질 수 있다는 것이고, 프로토 타입 객체도 만들어낸다는 것을 의미**한다.

이러한 문제를 해결하기 위해서 **ES6 에서는 함수를 사용목적에 따라 세가지로 분류**했다.

| ES6 Function    | constructor | prototype | super | arguments |
| --------------- | ----------- | --------- | ----- | --------- |
| Normal Function | y           | y         | x     | y         |
| Method          | x           | x         | y     | y         |
| Arrow           | x.          | x         | x     | x         |

## Method

아까의 자바스크립트 코드를 다시한번 보자.

```javascript=
var person = {
    age: 99,
    myAge: function() { return this.age }
}

console.log(person.myAge()); // 99
console.log(new person.myAge());
```

위에서 말했듯이 **객체안의 function 이니 myAge() 는 메소드 일까?**
Method 라면 new 생성자를 써주었을때 Error 를 뿜어야 할것이다.
하지만 아래와 같이 하면 `console.log(new person.myAge())` 실행되지 않고, TypeError 를 내뿜는다고 생각하면, 아니다 아래와 같이 잘 나온다.

![](https://i.imgur.com/b97PEd7.png)

위의 로직이 작동하는 이유는 뭘까? JavaScript 의 Method 는 오직 축약표현으로 서술한 것을 Method 라고 정의했기 때문이다. 따라서 우리가 저 코드가 TypeError 를 뿜게 하기 위해서는 아래와 같이 코드를 바꿔야 한다.

```javascript=
var person = {
    age: 99,
    myAge() { return this.age }
}

console.log(person.myAge()); // 99
console.log(new person.myAge());
```

이렇게 바꾸면 아래와 같은 결과가 나온다.

![](https://i.imgur.com/eBnhPz7.png)

또한 위에서 봤듯이 메소드는 property 를 가지고 있지도 않을 것이다.

```javascript=
console.log(person.myAge.hasOwnProperty('property')); // false
```

위와 같이 입력하면 false 가 나온다. **이는 당연한 결과**이다. **method 는 객체 내의 interface 처럼 이용**되어야 하는데, **method 가 property 를 가지고, 프로토타입 객체마저 만들어 낸다면, 이는 객체를 훼손시킬 수 있거나, 모순에 해당한다고 생각**한다.

다만 기존의 객체지향 언어들처럼 super 를 관리하기 위해 `[[HomeObject]]` 를 갖는다.

```javascript=
const rocket = {
  boom() {
    return 'Hello Boom!';
  }
}

const rocketCenter = {
  __proto__: rocket,

  sayBoom() {
    return super.boom();
  }
}

console.log(rocketCenter.boom()); // 'Hello Boom!'
```

위에서 말했듯이 메소드를 축약형으로 쓰지않으면 이건 불가능하다. 축약형이 아닌 함수는 메소드가 아니므로 `[[HomeObejct]]` 를 가지지 않기 때문이다.

## Arrow Function

화살표 함수는 JavaScript 를 하면 많이 사용하게 되는 함수이다.
아래와 같이 사용 가능하다.

```javascript=
const add = (x,y) => x + 2;
```

**화살표 함수 또한 일급 객체로 다뤄지기에 아래와 같은 방법으로 서술이 가능**하다.

```javascript=
[1,2,3].map(function (v) {
    return v*2;
});

[1,2,3].map(v => v * 2);
```

화살표 함수는 this 의 독특한 방식때문에 많이 쓰이는데, 그 이유는 화살표 함수의 this 는 가장 가까운 상위의 this 를 참조하기 때문이다. 예를 들면 아래와 같은 코드를 한번 보자.

```javascript=
class Prefixer {

    constructor(prefix) {
        this.prefix = prefix;
    }

    add(arr) {
        return arr.map(function (item) {
            return this.prefix + item;
        })
    }

}

const prefixer = new Prefixer('-webkit-');

console.log(prefixer.add(['transition', 'user-select']));
```

라고 썼을때 우리는 [-webkit-transition, -webkit-user-select] 를 기대하지만 결과는 그렇게 나오지 않는다. 왜냐하면 **map 함수안의 this 는 map 콜백 함수를 일반 함수로 호출하기 때문에 undefined 이다.**

그래서 이런 경우 const that = this; 와 같은 문법을 통해서 극복해야만 했다.
예를 들면 아래와 같이 말이다.

```javascript=
class Prefixer {

    constructor(prefix) {
        this.prefix = prefix;
    }

    add(arr) {
        const that = this;
        return arr.map(function (item) {
            return that.prefix + item;
        })
    }

}
```

이런 문제가 콜백 함수 내부의 this 문제인데, 이제는 화살표 함수를 통해서 이를 극복 가능하게 되었다.

```javascript=
class Prefixer {

    constructor(prefix) {
        this.prefix = prefix;
    }

    add(arr) {
        return arr.map((item) => this.prefix + item)
    }

}

const prefixer = new Prefixer('-webkit-');

console.log(prefixer.add(['transition', 'user-select']));
```

이런식으로 적어주면 잘 동작되고 우리가 예상한 결과값이 도출된다.
위와 같이 **화살표 함수의 this 는 상위 스코프의 this 를 그대로 참조**한다. 이를 **lexical this** 라고 부른다.
