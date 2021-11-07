# 이벤트

## 이벤트 타입

**버블링이 되지 않는 이벤트 타입**

- mouseenter
- mouseleave
- focus
- blur

**특정 상황마다 동작방식이 다른 이벤트 타입**

- keydown
   모든 키를 눌렀을 때, 발생한다.
   하지만 문자, 숫자, 특수 문자, 엔터 키를 눌렀을 때에는 연속적으로 발생한다.

## 커스텅이벤트

Event, UIEvent, MouseEvent 등의 생성자 함수를 통해 생성할 수 있다.

**예시**

```js
const keyboardEvent = new KeyboardEvent('keyup');
console.log(keyboardEvent.type); // keyup
```

커스텀이벤트의 버블링과 취소가능 여부는 두 번째 인수로 전달하는 객체를 통해 제어할 수 있다. (기본값은 불가)

```js
const keyboardEvent = new KeyboardEvent('keyup', {
  bubbles: true,
  cancelable: true
});

```
