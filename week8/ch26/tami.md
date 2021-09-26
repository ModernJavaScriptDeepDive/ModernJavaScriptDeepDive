# 📒26 ES6 함수의 추가 기능

#### 함수 호출 시 차이
|ES6 이전|ES6|
|------|---|
|메서드 === 생성자 함수 |메서드,화살표 함수(`new`) !== 생성자 함수 |

## ES 6 이전
ES6 이전의 함수는 객체에 바인딩된 함수도 생성자함수로 호출할 수 있었으며, 이는 그 함수가 생성자로 호출할 때마다 각각의 **prototype 프로퍼티** 와 **프로토타입 객체**를 생성하기 때문에 불필요한 프로토타입 객체가 생성되는 성능상 단점이 존재했다.

(콜백함수 ex)`map` 도 마찬가지)

## ES 6 이후

### 메서드
foo : 메서드
bar : 일반함수
```javascript=
const a = {
    x:1,
    foo() {return this.x},
    bar: function(){return this.x}
}
```
- ES6 이후 메서드와 화살표 함수는 `non-constructor` 
- ES6 메서드는 `super`키워드 사용 가능 (내부슬롯 `[[HomeObject]]`를 가짐)
-메서드의 constructor 기능을 제거

### 화살표 함수
- 콜백함수 내부의 `this`가 전역객체를 가리키는 일 해결 가능
- 중괄호(`{}`) 생략이 가능하지만 표현식이 아닌 문의 경우 생략 불가능
```javascript=
// 불가
const foo = ()=> const x =1 

// 가능
const foo = () =>{return const x = 1}
```

- 객체 리터럴 시 소괄호로 감싸기
```javascript=
const foo = () =>({id,pw})
foo(1,2)
// {id:1, pw:2}
```

#### 일반 함수와 비교했을 때의 화살표 함수 
1. non-constructor 인스턴스 생성 불가능
2. 중복 매개변수 이름 선언 불가 (strict-mode 시 둘 다 불가)
3. 자체 this 바인딩 없음 (스코프 체인중 가장 가까운 상위함수(화살표함수 x)참조) == lexical this 
```javascript=
() => this.x
(function (){ return this.x}).bind(this)
```
#### ⭐️ lexical this
화살표함수의 this가 함수 정의된 위치에 의해 결정되는 것

메서드 정의시에는 화살표 함수보다 ES6메서드 축약표현을 사용하는 것이 좋다.

- 함수 자체의 `super`,`arguments` 바인딩 없음

#### ⭐️ arguments
함수 호출 시 전달된 인수들의 정보를 담고 있는 유사배열객체
매개변수를 확정할 수 없는 가변인자 함수 구현시 유용
```javascript=
function foo(){
    console.log(arguments)
}
foo(1,2)
// {length:3, '0':1,'1',2}
```


### Rest 파라미터 `...`
매개변수에 할당된 나머지 인수들의 배열
- 마지막 파라미터 여야함
- 1개만 선언 가능 
```javascript=
function foo(a,...rest){}
foo(1,2,3,4)
// a= 1
// rest = [2,3,4]
```
