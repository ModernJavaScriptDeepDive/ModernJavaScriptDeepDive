## 12장. 함수

자바스크립트의 함수는 객체 타입의 값이다. 함수도 함수 리터럴(표현식)로 생성 가능

함수는 함수 이름으로 호출하는 것이 아니라, **함수 객체를 가리키는 식별자로 호출**한다.

```jsx
// 변수에 함수 리터럴을 할당한 예시
var f = function add(x, y) {
	return x + y;
};
```

- 함수 리터럴 : function 키워드, 함수 이름, 매개변수 목록, 함수 몸체로 구성
    - 함수 선언문과 동일한 구성임
    - 함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자다. 함수 이름은 생략할 수 있다.
        
        ![image](https://user-images.githubusercontent.com/60209518/126053645-77b1b845-0c4c-486a-833e-6aaeca3ebc20.png)

- 함수 리터럴은 평가되어 값을 생성하고, 이 값은 객체다. (👈 자바스크립트의 중요한 특징) 일반 객체와는 다르게 함수 객체만의 고유한 프로퍼티를 갖는다.

## 함수 정의

4가지 방법이 있다. 

> 참고: ECMAScript 사양에서 변수는 선언(declaration), 함수는 정의(definition)라고 표현. **함수 선언문이 평가되면 함수 이름과 동일한 이름의 식별자가 암묵적으로 생성**되고 **함수 객체가 할당**된다.

- 함수 선언문
- 함수 표현식
- Function 생성자 함수
- 화살표 함수 (ES6)

1. **함수 선언문**
    1. 함수 리터럴과 형태가 동일. 차이점은 함수 리터럴은 함수 이름을 생략할 수 있는 반면 함수 선언문은 생략할 수 없다.
    2. 표현식이 아닌 문 (크롬 개발자도구에서 완료값 `undefined` 가 출력됨)
    3. 근데 변수에 할당할 수 있으면 표현식 아니야?! 아래 코드 참고

        ```jsx
        // 엥 근데 함수 선언문.. 변수에 할당할 수 있잖아?
        var add = function add(x, y) {
        	return x + y;
        };

        console.log(add(2, 5)); // 7
        ```

    4. 이렇게 동작하는 이유는, 기명 함수 리터럴은 **코드의 문맥**에 따라 함수 선언문 또는 함수 리터럴 표현식 두 가지로 해석되기 때문
    5. 따라서 함수 리터럴을 단독으로 사용(피연산자로 사용하지 않는 경우)하면 **함수 선언문**으로 해석, 함수 리터럴이 값으로 평가되어야 하는 문맥(변수에 할당하거나 피연산자로 사용하는 경우)에서는 **함수 리터럴 표현식**으로 해석한다.
    6. 함수는 함수 이름으로 호출하는 것이 아니라 함수 객체를 가리키는 식별자로 호출하는 것!!
    7. 자바스크립트 엔진은 함수 선언문을 함수 표현식으로 변환해 함수 객체를 생성하는 셈. 함수 선언문과 함수 표현식의 차이점은 무엇일까?
2. **함수 표현식**
    1. 값의 성질을 갖는 객체를 일급 객체라고 한다. 자바스크립트의 함수는 일급 객체다. 함수를 값처럼 사용 가능
    2. 즉, 함수 리터럴로 생성한 **함수 객체를 변수에 할당**할 수 있는데 이러한 함수 정의 방식을 **함수 표현식** (function expression) 이라 한다.
    3. 변수에 할당하면 코드의 문맥에 따라 함수가 피연산자로 사용됐기 때문에 함수 리터럴 표현식으로 해석된다. 함수 리터럴의 함수 이름은 생략할 수 있다. 따라서 다음과 같이 함수 표현식을 쓸 수 있다.

        ```jsx
        var add = function(x, y) {
        	return x + y;
        };
        ```

3. **함수 호이스팅 vs 변수 호이스팅**
    1. 함수 선언문과 함수 표현식의 차이는 함수 호이스팅, 변수 호이스팅 이다.
    2. 함수 선언문
        1. 런타임 이전에 함수 객체가 먼저 생성된다. 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하고, 식별자에 생성된 함수 객체를 할당한다. 함수 객체로 초기화된다는 뜻임! (참고 - 함수 몸체 내부에 사용된 변수들은 함수가 호출됐을 때 선언됨)
        2. 런타임에는 이미 함수 객체가 생성되어 있고 함수 이름과 동일한 식별자에 할당까지 완료된 상태
        3. 함수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 것을 함수 호이스팅이라고 한다.
    3. 함수 표현식 (var 사용 시)
        1. var 키워드로 선언된 변수는 undefined로 초기화된다.
        2. 함수 표현식의 함수 리터럴은 런타임에 평가되어 함수 객체가 된다.
        3. 변수 호이스팅 발생
    4. 차이점 : var 키워드를 사용한 변수 선언문 이전에 변수를 참조하면 변수 호이스팅에 의해 undefined로 평가되지만, 함수 선언문으로 정의한 함수를 선언문 이전에 호출하면 함수 호이스팅에 의해 호출이 가능하다.
4. **Function 생성자 함수**
    1. 일반적이지 않고 바람직하지도 않다. 클로저도 생성하지 않음. 몰라도 될 듯..
5. **화살표 함수**
    1. 항상 익명 함수로 정의
    2. 기존의 함수 선언문 또는 함수 표현식을 완전히 대체하기 위해 디자인된 것은 아니다. 기존의 함수보다 표현만 간략한 것이 아니라 **내부 동작 또한 간략화**되어 있다.
    3. 화살표 함수의 특징 - 자세한 건 26.3절 "화살표 함수"에서 다룸
        1. 생성자 함수로 사용할 수 없다.
        2. 기존 함수와 this 바인딩 방식이 다르다.
        3. prototype 프로퍼티가 없다.
        4. arguments 객체를 생성하지 않는다.

## 함수 호출

- 함수를 가리키는 식별자와 함수 호출 연산자 `()` 로 호출
- 함수를 호출하면 현재의 실행 흐름을 중단하고 호출된 함수로 실행 흐름을 옮김
- 매개변수(parameters)에 인수(arguments)가 순서대로 할당되고 함수 몸체의 문들이 실행되기 시작한다.
- parameter 개수 > argument 개수 : arg 부족해서 할당되지 않은 param의 값은 undefined
- parameter 개수 < argument 개수 : 초과된 arg는 arguments 객체의 프로퍼티로 보관된다.

## 다양한 함수의 형태

- 즉시 실행 함수
- 재귀 함수
- 중첩 함수
- 콜백 함수
    - 함수의 매개변수를 통해 다른 함수의 내부로 전달되는 함수
    - 고차 함수: 매개변수를 통해 함수의 외부에서 콜백 함수를 전달받은 함수 또는 함수를 반환하는 함수
- 순수 함수, 비순수 함수
    - 순수함수는 매개변수(param)를 통해 함수 내부로 전달된 **인수(arg)에게만 의존**해 반환값을 만든다.
    - 매개변수를 통해 객체를 전달받으면 비순수 함수가 된다. 참조만 전달하는 거니까. 객체 리터럴로 전달하면 괜찮겠지??? (리액트 방식)
