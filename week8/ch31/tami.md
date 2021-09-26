# 📒31 RegExp
regular expression
일정한 패턴을 가진 문자열의 집합을 표현하기 위해 사용하는 **형식 언어**
![](https://i.imgur.com/2M31JSD.png)

패턴과 플래그로 구성
플래그 `g i m u y`
```javascript=
const a = 'hi tami';
const regexp = /tami/i

regexp.test(a) //true
```
## RegExp 메서드
RegExp.prototype.____

|메서드|매칭 결과 반환값|
|------|---|
|exec|배열 (첫번째 매칭만)|
|teset|boolean|
|match|배열 (g 이면 전부)|

## 플래그

|플래그|의미|
|------|---|
|i|대소문자 구별 X|
|g|전역 검색|
|m|문자열 행 바뀌어도 검색|
|플래그 없음|대소문자 구별 O|


## 다양한 예시
```javascript=
// 임의 문자열 
const ex = 'hi tami'
const regExp = /.../g
ex.match(regExp) // ["hi ", "tam"]

// 개수
const ex = 'aa,aaa,aaa,bb,aaaa'
const regExp = /a{3}/g //3번
const regExp = /a{3,}/g //3번 이상
const regExp = /a+/g //1번 이상


ex.match(regExp) // ['aaa','aaa']
ex.match(regExp) // ['aaa','aaa','aaaa']
ex.match(regExp) // ['a',aaa','aaa','aaaa']

// 숫자
const regExp = /[0-9]/g
const regExp = /\d/g

// 숫자가 아님 
const regExp = /^[0-9]/g
const regExp = /\D/g

// 알파벳, 숫자, 언더스코어
const regExp = /[A-za-z0-9_]/

const regExp = /\w/
const regExp = /\W/

// 시작과 끝
const ex = 'http://tamiworld.com'

const regExp = /^http/ //시작하는지
const regExp = /com$/ //끝나는지

ex.test(regExp) // true
ex.test(regExp) // true

// 공백 
const regExp = /^[\s]+/ // 하나 이상의 공백으로 시작


```

### ^구분 
[]안에 들어가면 `not`의 의미 밖으로 나오면 시작의 의미
|``/^[a]/``|``/[^a]/``|
|------|---|
|a로 시작하는가|a를 포함하는가|

#### +와 +를 하지 않았을 때의 차이
![](https://i.imgur.com/VjM9YID.png)


### 자주 사용하는 정규표현식
```javascript=
공백으로 시작하는지
/^[/s]+/

알파벳 대소문자 or 숫자로 시작 끝나며 4~10자리
/^[A-Za-z0-9]{4,10}$/

핸드폰
/\d{3}-\d{3,4}-\d{4}$/

특수문자 포함 여부
/[A-Za-z0-9]/gi

```

#### 막간 퀴즈 
우리가 실제 자주 사용할 정규표현식은?

휴대폰번호
010-1111-2222

메일주소
a@gmail.com

yyyymmdd
1992-08-20




휴대폰

`(?:(010-\d{4})|(01[1|6|7|8|9]-\d{3,4}))-(\d{4})`

메일주소
`^[0-9\-]([-_.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_.]?[0-9a-zA-Z])*.[a-zA-Z]{2,3}`

yyyymmdd
`^((19|20)\d{2})(0[1-9]|1[012])(0[1-9]|[12][0-9]|3[0-1])`
