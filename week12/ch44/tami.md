# 📒 44 - REST API
RESTful하다 = REST의 기본 원칙을 지킨 서비스 디자인

## REST API
자원 `URI`엔드포인트
행위 HTTP 요청 메서드
표현 `payload` 자원에 대한 행위의 구체적 내용

- URI는 리소스를 표현하는데 집중하며 행위를 표현하지 않는다
- 행위는 요청 메서드를 통해 표현

```
// bad
GET/getTodos/1
// good
GET/todos/1
```
