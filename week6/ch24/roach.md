# Closure

**Closure** 는 JavaScript 의 개념이 아니다. FP 에서 자주 등장하는, **함수와 함수과 선언 되어 있는 렉시컬 스코프 환경**을 뜻한다. 예를 들어 아래의 Func 를 보자

```javascript

const x = 1;

funciton outerFunc() {

    const x = 10;
    function innerFunc() {
        console.log(x); // 10
    }
    innerFunc();
}

outerFunc();

```

위의 식은 우리의 생각대로 10으로 잘 작동 한다. 하지만 아래와 같은 Func 를 보자

```javascript
const x = 1;

function outerFunc() {
  const x = 10;
  innerFunc();
}

function innerFunc() {
  console.log(x); // 1
}

outerFunc();
```

이는 같은 실행동작인데도 불구하고, 다른 결과를 도출해낸다. 이는 자바스크립트의 렉시컬 스코프 때문이다.
즉 **렉시컬 환경의 '외부 렉시컬 환경에 대한 참조' 는 함수 정의가 평가되는 시점에 결정**되는 것이다.
이때 저장된 '외부 렉시컬 환경에 대한 참조' 를 `[[Environment]]` 에 저장한다.

```javascript
const x = 1;

function outer() {
  const x = 10;
  const inner = function () {
    console.log(x);
  };
  return inner;
}

const innerFunc = outer();
innerFunc();
```

이 경우 메모리상에서 outer 는 innerFunc 에게 값을 전달해 주는 순간 LifeCycle 이 종료되어야 한다.
하지만, innerFunc 에서 outer 안의 X 를 참조해야 하므로, 해당 Memory 공간에서 제거되지 않는다.
이러한 중첩함수를 Closure 라고 한다.

놀라운점은 Closure 는 만약 outer 에서 내가 x 만 기억한다면, Closure 에 x 의 값만 남게 된다.. 최적화가 엄청나긴하다.
Closure 또한 클래스 언어의 Getter / Setter 처럼 내부 State 를 안전하게 관리하기 위해 주로 사용된다.

또 나오는 캡슐화와 정보은닉..💀
