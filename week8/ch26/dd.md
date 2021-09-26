# ES6 함수의 추가 기능

ES6 이전 모든 함수는 일반 함수/생성자 함수로서 모두 호출 할 수 있었다. 다시말해 callable이면서 constructor이다.

이는 메서드도 calllabel이면서 constructor라는 거고, prototype 프로퍼티를 가진다. 이는 성능적 불이익을 발생시킨다.

목적에 따른 명확한 구분이 없었기 때문에 ES6에서는 일반함수/메서드/화살표 함수로 구분해서 constructor/prototype/super/arguments 속성 유무를 나누었다.

## 메서드

ES6 사양에서는 메서드 축약 표현으로 정의된 함수만을 의미한다. 메서드는 인스턴스를 생성할 수 없는 non-constructor이다. 따라서 prototype 프로퍼티도 없고, 프로토타입을 생성하지도 않는다. 

대신 super 키워드를 사용할 수 있다. [[HomeObject]] 슬롯 





## 화살표 함수

- 생성자 함수로 사용할 수 없다.
- strict mode가 아닐지라도 매개변수 이름을 중복할 수 없다. (일반 함수는 가능하다)
- 함수 자체의 this, arguments, super, new.target 바인딩을 갖지 않는다. 

- 화살표 함수의 this는 호출 방식이 아니라 정의된 위치, 즉 **상위 스코프의 this를 그대로 참조한다.** lexical this

- 따라서 **메서드를 화살표함수로 정의하지 마라**

- 마찬가지로 super,arguments 바인딩도 갖지 않기 때문에 this와 마찬가지로 상위 스코프의 super,arguments 를 참조한다.

