# 생성자 함수에 의한 객체 생성

> 생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킨다.

## this 바인딩

함수 호출 방식에 따라 동적으로 결정

| 함수 호출 방식 | this 바인딩               |
| -------------- | ------------------------- |
| 일반함수 호출  | 전역 객체(window, global) |
| 메서드 호출    | 메서드를 호출한 객체      |
| 생성자 호출    | 미래에 생성할 인스턴스    |

## 인스턴스 생성과 this 바인딩

1. new 연산자와 함께 생성자 함수를 호출
2. 암묵적으로 빈 객체(인스턴스)가 생성
3. 이 객체는 this에 바인딩
4. 생성자 함수에 기술되어있는 코드가 한 줄씩 실행되어 this에 바인딩된 인스턴스 초기화
5. 인스턴스 반환

## 함수의 내부 메서드 [[Call]]과 [[Contsruct]]

함수는 일반 함수로서 호출되면 [[Call]] 메서드가 호출,  
new 연산자와 함께 호출되면 [[Contruct]] 메서드가 호출.

> [[Call]]을 갖는 객체를 callable이라 한다.  
> 함수는 호출할 수 있어야하므로 반드시 callable이다.
>
> [[Contruct]]를 갖는 객체를 contructor, 갖지 않으면 non-contructor
>
> - 모자스 :lizard:

## contructor와 non-contructor의 구분

자바스크립트 엔진은 함수 정의를 평가하여 함수 객체를 생성할 때, 정의 방식에 따라 구분한다.

**contructor**

- 함수 선언문
  > function foo() {}
- 함수 표현식
  > const foo = function() {};
- 클래스
  > const foo = {
  > x: function () {}
  > }

**non-contructor**

- 메서드 _ES6 축약표현만 인정_
  > const foo = {
  > x() {}
  > }
- 화살표 함수
  > const arrow = () => {}

## new.target

생성자 함수가 의도에 맞게 호출되도록 처리할 수 있다.

```js
function Circle(radius) {
  if (!new.target) return new Circle(radius);
  // 스코프 세이프 생성자 패턴으로도 구현 가능.
  // !(this instanceof Circle)

  this.radius = radius;
}
```
