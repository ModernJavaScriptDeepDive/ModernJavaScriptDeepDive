# 이벤트

## 이벤트 핸들러 어트리뷰트 방식

> HTML 요소의 어트리뷰트에 이벤트 핸들러를 직접 할당한다

```html
<button onclick="fn('params')">Click</button>
```

- 이 방식은 이전에 사용하던 방식으로 지금은 사용하지 않는다. HTMl과 JS의 관심사를 분리하기 위해

- 하지만 React와 같은 CBD(Component Based Development) 프레임워크는 HTML, CSS, JS를 **뷰를 구성하기 위한 요소**로 동등하게 보기 때문에, 관심사가 다르다고 생각하지 않는다. 따라서, 이벤트 핸들러 어트리뷰트 방식으로 이벤트를 처리한다.

- 이 방식에서는 핸들러가 이벤트 객체를 전달받으려면 반드시 `event` 라는 이름이어야한다. 관례적으로 e를 사용하는건 다른 방식에서만 가능하다

## 이벤트 핸들러 프로퍼티 방식

> DOM 노드 객체의 이벤트 핸들러 프로퍼티에 핸들러를 할당한다.

```javascript
const $button = document.querySelector("button");

$button.onclick = function () {
  console.log("button click");
};
```

- 앞선 이벤트 핸들러 어트리뷰트 방식도 결과적으로 노드 객체의 프로퍼티에 할당하는 것과 동일하다

- 프로퍼티 방식은 HTMl과 JS의 관심사를 분리하는 장점이 있지만, 하나의 프로퍼티에 하나의 핸들러만 바인딩해야하는 단점이 있다.

## addEventListener 메서드 방식

>

```javascript
const $button = document.querySelector("button");

$button.addEventListener("click", () => {
  console.log("click");
});
```

- 프로퍼티 방식과 addEventListener는 서로 영향을 주지 않는다. 따라서 둘 다 핸들러를 등록할 경우 같은 이벤트에 대해 두 가지 모두 호출된다.

- 프로퍼티 방식은 같은 이벤트에 대해 하나의 핸들러밖에 등록할 수 없지만 addEventListener 방식은 같은 이벤트에 대해 여러 핸들러를 등록할 수 있다. 참고로 등록 순서에 따라 호출된다.

- 하지만 핸들러의 참조가 동일하다면 하나의 핸들러만 등록된다.

## 이벤트 객체 타입

- Object => Event가 최상위 객체이다.

- 발생한 이벤트에 따라 Event를 상속한 각자의 이벤트 객체가 생성, 핸들러에 전달된다.

## 이벤트 발생 순서

- 이벤트가 발생하면 생성된 이벤트 객체는 **window에서 시작해서 이벤트 타깃으로 전파된다.**(캡처링) 그리고 다시 window 방향으로 전파되는게 버블링이다.

- addEventListener로 등록한 핸들러는 기본적으로 버블링 단계의 이벤트만 캡쳐할 수 있고, 세 번째 인자로 true를 전달해야 캡쳐링 단계의 이벤트를 캐치할 수 있다.

## 버블링 되지 않는 이벤트

- `foucs` / `blur` => `focusin` / `focusout`
- `load` / `unload` / `abort` / `error`
- `mouseenter` / `mouseleave` => `mouseover` / `mouseout`

- 위 이벤트는 버블링되지 않으므로 타깃 상위 요소에서 캡쳐하려면 캡쳐링 단계에서 캡쳐해야한다.
- 혹은 => 우측에 있는 이벤트로 대체하면 버블링 단계에서 캡쳐할 수 있다.
- 따라서 캡쳐링 단계에서 이벤트를 캐치해야할 경우는 거의 없다. 