# Ajax

> 자바스크립트를 사용하여 브라우저가 서버에서 비동기 방식으로 데이터를 요청하고, 서버가 응답한 데이터를 수신하여 웹페이지를 동적으로 갱신하는 프로그래밍 방식을 맗나다.

- 이전과는 다르게 필요한 부분만 변경함

## JSON

> 클라이언트와 서버 간의 HTTP 통신을 위한 텍스트 데이터 포맷

## XMLHttpRequest

> 서버와 상호작용 하기 위해 사용되는 객체, 주로 AJAX에 사용

```js
const xhr = new XMLRequest();
```

### XMLHttpRequest 프로퍼티

1. readyState : 요청의 현재 상태를 나타내는 정수
   - 0 : 생성만 한 상태
   - 1 : open()을 호출한 상태
   - 2 : send()를 호출한 상태
   - 3 : 다운로드 중인 상태
   - 4 : 완료된 상태
2. status : HTTP 상태 코드
3. responseType : HTTP 응답 타입 (json, text, blob, document)

### HTTP 요청 전송

**예제**
```js

// XMLHttpRequest
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://jsonplaceholder.typicode.com/todos/1');
xhr.send();
xhr.onloadend = () => {
  console.log(JSON.parse(xhr.response));
};

// fetch
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(json => console.log(json))
```