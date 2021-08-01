# 📒22 this
## this

- 자신이 생성할 인스턴스를 참조할 수 있는 식별자
- `this`를 통해 생성할 인스턴스의 프로퍼티와 메서드를 참조할 수 있다.
- JS엔진에 의해 암묵적으로 생성된다.
```javascript=
funciont Foo = {
    this.a = a;
    
    Foo.prototype.getA = funciton()    {
        return a*a
    }
}
Foo = new foo(3)
```
`Foo`는 foo를 참조할 식별자 `this`가 필요

## this 바인딩
this바인딩은 함수 호출 방식에 의해 동적으로 결정
`바인딩`: 식별자와 값을 연결하는 과정 
(변수선언: a=10 a와 10을 저장할 메모리 공간을 바인딩하는 것)
- JAVA,C++과 다르게 JS의 `this`는 함수가 호출되는 방식에 따라 동적으로 결정된다
- **strict mode**에 따라 달라짐

```javascript=
funciton foo(){
    console.log(this)
    //일반모드 : window
    //strict mode: undefined
}
```

###  함수 호출에 따른 this 바인딩
```javascript=
const obj = {foo}
const bar = { a: 10}

// 1) 일반함수 호출: window : 전역 객체
foo()

// 2) 메서드 호출: obj : 호출한 객체
obj.foo()

//3) 생성자 함수 호출: foo{} : 생성할 인스턴스
new foo()

//4) Function.prototype.apply call bind
foo.call(bar) //bar
foo.apply(bar) //ba
foo.bind(bar)() //bar

```

일반함수로 호출된 함수의 내부의 this에는 전역객체가 바인딩 되는데,
내부 중첩함수,콜백함수가 가리키는 this가 일반함수와 다르면 안되기때문에 바인딩을 해준다.
메서드의 this와 메서드 내부의 중첩,콜백함수의 this가 불일치할 때 사용한다.

```javascript=
setTimeout({}.bind(this),100)
setTimeout(()=>console.log(this.value),100) //화살표함수 내부 this = 상위 scope this
```

메서드는 객체에 포함된 것이 아닌 독립적으로 존재하는 별도의 객체

### call,apply
인수로 전달하는 객체를 this로 바인딩 하며 함수를 호출하는 것 
### bind
this로 사용할 객체를 전달한다.


####  bind와 call,apply는 어떤 점이 다른가?

3가지 다 **this로 사용할 객체를** 전달하여 바인딩하는 공통점이 잇지만 
call과 bind는 객체를 전달하며 함수를 호출하지만 
bind는 this로 사용할 객체를 전달하는 기능만 합니다.
특히 메서드의 this와 메서드 내부의 중첩,콜백함수의 this가 불일치할 때 사용한다.

#### this가 무엇인가요? [❓질문] 
자신이 속한 객체와 생성할 인스턴스를 가리키는 참조변수를 말합니다.

#### this가 필요한 이유 [❓질문] 
메서드는 자신이 속한 객체의 상태를 참조하고 변경할 수 있어야 하는데 이를 위해서는 
자식이 속한 객체와 생성할 인스턴스를 가리키는 참조변수인 this가 있어야 합니다.

#### 렉시컬스코프와 this 바인딩은 결정 시기가 다르다
렉시컬스코프는 함수가 선언된 후 객체가 생성되는 시점에 스코프가 결정되지만,
this바인딩은 함수를 호출할 때 결정이 됩니다.
