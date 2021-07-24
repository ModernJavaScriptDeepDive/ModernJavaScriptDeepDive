#  📒10-Object 객체 리터럴
자바스크립트는 객체(object) 기반의 프로그래밍 언어

객체는 **mutable** (변경 가능한 값) 이다.
기본적으로 거의 모든것이 객체이므로 변경이 가능하다.  

- 객체는 property로 구성된다
- JS의 함수도 객체로 취급 : 함수 = property

`프로퍼티` : 객체의 상태를 나타내는 값(data)
`메서드`: 
- 프로퍼티를 참조하고 조작하는 동작
- property값이 함수인 경우  
- 객체에 묶여있는 함수

ex) increase : `메서드`  num :`프로퍼티`
```javascript=
var counter = {
num : 0,
increase : function(){
    this.num++
    }
};
```

  
|키워드|내용|예시|
|------|---|---|
|immutable|변경 불가능한 값|const 변수, Object.freeze 객체|
|mutable|변경 가능한 값|객체,함수,배열,정규표현식|
## variable vs Object
`variable` :  변수는 값 자체가 메모리에 저장된다
![](https://i.imgur.com/89jty6U.png)

`Object` : 객체는 Object를 가리키는 reference가 메모리에 저장된다.

![](https://i.imgur.com/mVRMNMW.png)
[출처](https://www.youtube.com/channel/UC_4u-bXaba7yrRz_6x6kb_w)
## 객체 생성
자바스크립트는 프로토타입 언어로 다양한 객체 생성 방법을 지원  
1) 객체 리터럴
2) Object 생성자 함수
3) 생성자 함수
4) Object.creater
5) 클래스 (ES6)

|키워드|예시|
|------|---|
|객체리터럴|`const todo ={content:'hi'}`|
|생성자 함수|`const todo = new Todo`|



## 프로퍼티
#### 객체 프로퍼티 값 접근하는 두가지 방법

대괄호로 접근할 시엔 꼭 `'`로 감싼 문자열이어야 함
|키워드|예시|
|------|---|
|마침표|`person.name`|
|대괄호|`person['name']`|

#### Node.js 와 브라우저 환경의 실행 결과 차이
브라우저 환경에는 기존 전역객체의 프로퍼티가 암묵적으로 존재하기 때문에 전역객체의 프로퍼티 이름을 사용하여 프로퍼티 값을 접근할 경우 브라우저와 결과가 다를 수 있다.

### 생성과 삭제
```javascript=
var person = {
    name : 'Tami',
}

//생성
person.age = 25 // {name:'Tami',age:'25'}

//삭제
delete person.age // {name: 'Tami'} 
```

### 프로퍼티 키 생략 가능 

```javascript=
const x=1, y=3;

const obj = {x,y}
//const obj = {x:x, y:y}
//obj = {x:1, y:3}

```
