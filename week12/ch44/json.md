# REST API

> REST는 HTTP를 기반으로 클라이언트가 서버의 리소스에 접근하는 방식을 규정한 아키텍처를 의미한다.

## REST API의 구성

**자원**, **행위**, **표현**의 3가지 요소로 구성되며, REST API만으로 HTTP 요청의 내용을 이해할 수 있다.

> 자원 : URI(엔드포인트)
> 행위 : HTTP 요청 메서드
> 표현 : 자원에 대한 행위의 구체적 내용(페이로드)

## REST API 설계 원칙

- URI는 리소스를 표현한다.
- 행위에 대한 정의는 HTTP 요청 메서드로 한다.

```md
# bad
GET /getTodos/1
GET /todos/show/1

# good
GET /todos/1
```
