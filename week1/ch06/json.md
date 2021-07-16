# 데이터 타입

## undefined 타입

자바스크립트 엔진은 변수를 선언하면 그 변수에 해당하는 메모리를 확보합니다.
그리고 그 메모리를 비워두지 않고 undefined를 할당하게 됩니다.

그러므로 변수를 참조했을 때, undefined이 반환된다면 할당이 이루어지지 않은 변수임을 확인할 수 있습니다.

> undefined는 예약어가 아니므로 식별자로 사용할 수 있습니다.
> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/undefined

```js
(function () {
  var undefined = 'foo';
  console.log(undefined, typeof undefined); // 'foo', 'string'
})();
```

> 물론 의도치 않은 에러가 발생할 수 있기에 사용하지 말아야 하는 패턴입니다.

## null 타입

null은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용합니다.

## undefined? null?

undefined는 변수에 할당이 이루어지지 않았음을 의미하며,  
null은 변수에 할당이 이루어졌음을 의미합니다.  
그러므로 개발자가 명시를 통해 빈 값을 표현할 때에는 null을 사용해야 합니다.
