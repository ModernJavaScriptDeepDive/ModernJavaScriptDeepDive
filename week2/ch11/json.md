# 원시 값과 객체의 비교

## 공유에 의한 전달

함수의 인수로 전달하는 객체는 사실 그 객체가 아니라 참조가 전달 되는 것.  
그래서 참조를 통해서 수정할 수 있지만 새로운 값을 할당하면 새로운 메모리를 참조하는 객체가 되므로 결과적으로 인수로 전달한 객체는 변경되지 않는다.

```js
function foo(a, b) {
  a = {
    name: 'aa',
  };
  b.name = 'bb';
}

function test() {
  let a = {
    name: 'a',
  };
  let b = {
    name: 'b',
  };
  foo(a, b);
  console.log(a.name); // 'aa' (x) 'a' (o)
  console.log(b.name); // 'bb'
}
test();
```

### 출처

> https://en.wikipedia.org/wiki/Evaluation_strategy > http://milooy.github.io/TIL/JavaScript/call-by-sharing.html#%E1%84%80%E1%85%A7%E1%86%AF%E1%84%85%E1%85%A9%E1%86%AB > https://stackoverflow.com/questions/518000/is-javascript-a-pass-by-reference-or-pass-by-value-language

---

## 얕은 복사와 깊은 복사

**얕은 복사**  
: 객체 자체를 복사하는 것. 객체가 가지고 있는 참조값을 복사한다.

**깊은 복사**  
: 객체의 실제 값을 복사하는 것. 객체가 가지고 있는 값을 복사한다.
