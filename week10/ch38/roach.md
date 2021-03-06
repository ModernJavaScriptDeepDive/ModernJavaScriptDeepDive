# 브라우저의 렌더링 과정

브라우저가 작성된 텍스트 문서를 어떻게 파싱하여 렌더링하는지 알아보자!

## Parsing

프로그래밍 언어의 문법에 맞게 작성된 텍스트 문서를 읽어 들여 실행하기 위해 텍스트 문서의 문자열을 토큰으로 분해하고
그 토크은으로 Parse Tree 만드는 것.

## Rendering

렌더링은 HTML, CSS, JS 로 작성된 문서를 브라우저에 시각적으로 출력하는 것.

## 브라우저 렌더링 과정

1. 브라우저는 HTML, CSS, JavaScript 파일 등 렌더링에 필요한 리소스를 요청하고 서버로부터 응답을 받는다.

2. 브라우저의 렌더링 엔진은 서버로부터 응답된 HTML 과 CSS 를 파싱하며 DOM과 CSSOM 을 생성하고, 이들을 결합하여 렌더 트리를 생성한다.

3. 브라우저의 자바스크립트 엔진은 서버로부터 자바스크립트를 파싱하여 AST 를 생성하고, 바이트 코드로 변환하여 실행한다.

4. 렌더 트리를 기반으로 HTML 요소의 레이아웃을 계싼하고 브라우저 화면에 HTML 요소를 페인팅한다.

## DOM

DOM 은 HTML 문서를 파싱해서 브라우저가 이해할 수 있는 자료구조인 DOM 으로 만드는 것.

## 리렌더가 되는 조건

1. 자바스크립트에 의한 노드 추가 삭제

2. 브라우저 창의 리사이징에 의한 뷰포트 크기 변경

3. HTML 요소의 레이아웃에 변경을 발생시키는 width/heigh 등등의 변경
