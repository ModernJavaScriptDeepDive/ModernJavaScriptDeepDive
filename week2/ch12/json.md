# 함수

> 함수는 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의하는 것

---

## 변수 선언과 함수 정의

> 변수는 선언하지만 함수는 정의한다고 표현했다.
> 함수 선언문이 평가되면 식별자가 암묵적으로 생성되고 함수 객체가 할당되기 때문

---

## 함수와 화살표 함수의 차이

1. 생성자 함수로 사용할 수 없다.
2. this 바인딩 방식이 다르다.
3. prototype 프로퍼티가 없다.
4. arguments 객체를 생성하지 않는다.

> 화살표 함수는 자신의 this가 없습니다.  
> 대신 화살표 함수를 둘러싸는 렉시컬 범위(lexical scope)의 this가 사용됩니다.  
> 화살표 함수는 일반 변수 조회 규칙(normal variable lookup rules)을 따릅니다.  
> 때문에 현재 범위에서 존재하지 않는 this를 찾을 때, 화살표 함수는 바로 바깥 범위에서 this를 찾는것으로 검색을 끝내게 됩니다.
>
> - [MDN 화살표 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions#%EB%B0%94%EC%9D%B8%EB%94%A9_%EB%90%98%EC%A7%80_%EC%95%8A%EC%9D%80_this)
