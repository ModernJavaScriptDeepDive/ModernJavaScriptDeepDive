# 자바스크립트란?

## Nodejs 

<br/>

### Node.js가 뭔가요? 

> Node.js는 **구글 V8 JS 엔진으로 빌드된 JS 런타임 환경**이다.

Node.js가 뭔가요? 라는 질문을 받았을 때, **런타임**이라고 대답할 수 있어야 한다.

#### 잘못 된 대답

- 자바스크립트로 백엔드 개발을 할 수 있게 해주는 것
- 자바스크립트 서버

위와 같은 대답은 틀린 얘기는 아니지만 <code>Node.js</code>로 할 수 있는 일 중 일부이지, Node.js 자체는 아님을 명심하자

<br/>

### 특징

- 비동기 I/O 지원
- 단일 스레드 이벤트 루프 기반
- request 처리 성능이 좋아서 SPA에 적합하다.
  - SPA는 실시간 데이터 처리를 위하 I/O가 빈번하게 발생하기 때문
- CPU 사용률이 높은 어플리케이션에는 권장되지 않음


<br/>

### 추가적으로 공부해야할 것

- 런타임은 뭘까? 컴파일 타임과의 차이를 설명할 수 있는가?

## JavaScript / ECMAScript

자바스크립트는 ECMAScript + 브라우저가 지원하는 <code>클라이언트 사이드 API</code>로 구성되어있다

### 클라이언트 사이드 API

- DOM
- BOM
- Canvas
- XMLHttpReqeust
- fetch
- requestAnimationFrame,
- SVG
- Web Storage,
- Wev Component,
- Web Worker
- 등등.. 

