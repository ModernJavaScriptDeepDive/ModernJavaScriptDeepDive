# Event Driven Programming

브라우저는 특정 사건이 발생하면 이를 감지하여 이벤트를 발생시킨다. <br>
예를 들면 클릭 이벤트, 키보드 입력 이벤트, 마우스 이동 이벤트 등이 있을 수 있다.

만약 이벤트에 해당 하는 어떤 일을 하고 싶다면 이벤트에 맵핑되는 반응을 추가해야 하는데, 이 반응이 **이벤트 핸들러**이다.

```html
<!DOCTYPE >
<html>
  <body>
    <button>Click!</button>
    <script>
      const $button = document.querySelector("button");
      $button.onclick = () => {
        alert("button click");
      };
    </script>
  </body>
</html>
```

위 예제를 보면 $button 요소의 **onclick 에 property 를 할당**했다. <br>
이처럼 이벤트와 그에 대응하는 함수를 통해 이벤트 중심으로 제어하여 프로그래밍하는 방식을 **이벤트 드리븐 프로그래밍**이라고 한다.

## addEventListener 메서드 방식

DOM Level 2 부터 도입된 EventTarget.prototype.addEventListener 메서드를 사용하여 이벤트 핸들러를 등록할 수 있다.

```html
<!DOCTYPE >
<html>
  <body>
    <button>Click!</button>
    <script>
      const $button = document.querySelector("button");
      $button.addEventListener("click", function () {
        console.log("button click");
      });
    </script>
  </body>
</html>
```

## 이벤트 객체

이벤트가 발생하면 이벤트에 관련한 다양한 정보를 담고 있는 이벤트 객체가 동적으로 생성된다. <br>
예를 들면 InputEvent, ClickEvent 등이 생길 수 있다.

## 커스텀 이벤트 발생

```javascript
const customEvent = new CustomEvent("foo");
```

생성된 커스텀 이벤트는 dispatchEvent 메서드로 디스패치를 할 수 있다.
