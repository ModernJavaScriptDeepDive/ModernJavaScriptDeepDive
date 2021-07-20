# 생성자 함수에 의한 객체 생성

- 생성자 함수가 new 키워드를 통해 객체 인스턴스를 생성하고, 생성자 함수 내부의 this가 이 객체에 바인딩 된다. 이 과정은 **런타임 이전에** 실행된다.

## 바인딩

> 바인딩이란 식별자와 값을 연결하는 과정을 의미한다. 

- 변수 선언은 변수 이름(식별자)과 메모리 공간의 주소를 바인딩하는 것이다.

## new. 생성자 함수의 반환 값

생성자 함수는 암묵적으로 this를 반환하지만, 명시적으로 **다른 객체**를 반환하면 그 객체가 반환된다. 원시값을 반환하면 무시되고 this가 반환된다.

## 함수는 호출 가능한 객체다

- 내부 슬롯 [[Environment]], [[FormalParameters]]

- 내부 메소드 [[Call]], [[Construct]] 등이 있다.

- 함수가 일반함수로서 호출되면 [[Call]], new 연산자와 함께 호출되면 [[Construct]]가 호출된다.


## 생성자 함수인지 아닌지 어케 구분?

> 함수의 정의 방식에 따라 constructor / non-constructor를 구분한다

- 함수 선언문 / 함수 표현식 (constructor)

- 화살표 함수 / 메서드 축약 표현 (non-constructor)

## new.target

> 메타 프로퍼티. 이 함수가 new 연산자와 함께 호출되었는지 알 수 있다

- new와 함께 생성자 함수로서 호출되면 new.target은 함수 자기 자신을 가리킴

- 일반 함수로서 호출되면 new.target은 undefined
