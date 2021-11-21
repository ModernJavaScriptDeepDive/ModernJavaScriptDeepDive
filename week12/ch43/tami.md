# 📒 43 - Ajax
## Ajax
JS를 사용해 서버에 비동기 데이터를 요청하고 수신하여 web을 동적으로 갱신하는 프로그래밍 방식

기존: 변경이 필요할 때 완전한 html 파일을 다시 요청하는 방식
변경: 변경이 필요한 부분적인 데이터만 요청후 받는 방식

## JSON
HTTP 통신을 위한 텍스트 데이터 포맷
- 객체 literal과 유사한 `key`,`value`로 이루어짐
- key는 ""로 묵여야 함
- 서버로 객체 전송 시 직렬화 과정이 필수적임 (JSON.Stringfy)
- 역직렬화 (문자열 -> 객체) JSON.parse
    
## XMLHttpRequest
`form` , `a` 로 HTTP 요청 기능 제공
Wep API 중 하나 

1. HTTP 요청 초기화
2. (선택)HTTP 요청 헤더값 설정
3. HTTP 요청 메서드로 전송

### HTTP 요청 메서드
GET, POST, PUT, PATCH, DELETE
GET: 쿼리 문자열로 전송 (`body`=null)
POST: 데이터`payload`를 `body`로 전송 

### Content-type
MIME 타입의 정보 표현
text, application, multipart
