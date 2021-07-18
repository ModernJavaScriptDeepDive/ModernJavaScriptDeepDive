## 15장. let, const 키워드와 블록 레벨 스코프

## let

- var 키워드로 선언한 변수는 런타임 이전에 자바스크립트 엔진에 의해 암묵적으로 "선언 단계"와 "초기화 단계"가 한 번에 진행되는 반면, **let 키워드로 선언한 변수는 "선언 단계"와 "초기화 단계"가 분리되어 진행된다.**
- 초기화 단계는 변수 선언문에 도달했을 때 실행!
- 초기화 단계 실행되기 이전에 변수에 접근하면 ReferenceError 발생
- 스코프의 시작 지점부터 초기화 단계 시작 지점 (변수 선언문) 까지 변수를 참조할 수 없음. 이 구간을 **Temporal Dead Zone; TDZ** 라고 한다.
- let 키워드로 선언한 변수도 호이스팅이 일어난다는 증거

    ```jsx
    let foo = 1; // 전역 변수
    {
    	console.log(foo); // ReferenceError: Cannot access 'foo' before initialization
    	let foo = 2; // 지역 변수
    }
    ```

- 자바스크립트는 var, let, const, function, function*, class 등 모든 선언을 호이스팅한다.
- let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다. window.foo와 같이 접근할 수 없다. let 전역 변수는 전역 렉시컬 환경의 선언적 환경 레코드 내에 존재하게 되는데, 이에 대해서는 23장. 실행컨텍스트에서 자세히..

    ```jsx
    let x = 1;
    console.log(window.x); // undefined
    console.log(x); // 1
    ```

## const

- const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.

    ```jsx
    const foo; // SyntaxError: Missing initializer in const declaration
    ```

- 재할당 금지
