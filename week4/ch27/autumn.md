# [27장. 배열](https://hongbi.notion.site/27-cde146e5b2bc40a4a5f583e579c2beee)

## 1. 배열이란?

- 자바스크립트에서 값으로 인정하는 모든 것은 배열의 요소가 될 수 있다.
- 배열은 **인덱스**와 **length** 프로퍼티를 갖기 때문에 for문을 통해 순차적으로 요소에 접근 가능
- 배열은 객체 타입이다.

    ```jsx
    typeof arr // object
    ```

- 배열은 배열 리터럴, Array 생성자 함수, `Array.of`, `Array.from` 메서드로 생성할 수 있다.
- 배열의 생성자 함수는 Array이며, 배열의 프로토타입 객체는 `Array.prototype`이다.
- 일반 객체와 배열을 구분하는 가장 명확한 차이는 "값의 순서"와 "length 프로퍼티"

## 2. 자바스크립트 배열은 배열이 아니다

- 자료구조에서 말하는 일반적인 배열은, 요소들이 하나의 데이터 타입으로 통일되어 있고 연속적으로 인접해 있다. 즉, 각 요소가 동일한 데이터 크기를 가지고 빈틈없이 연속적으로 이어져 있다. 이러한 배열을 밀집 배열(dense array)이라 한다.
- 그렇기 때문에 인덱스를 통해 단 한 번의 연산으로 임의의 요소에 접근할 수 있다. 시간복잡도 `O(1)`
- 자바스크립트의 배열은 일반적인 의미의 배열과 다르다. 배열 요소의 타입이 다를 수 있고 (= 각각의 메모리 공간이 동일한 크기를 갖지 않아도 됨), 연속적으로 이어져있지 않을 수도 있다.
- 배열 요소가 연속적으로 이어져 있지 않는 배열을 희소 배열(sparse array)이라 한다.
- **자바스크립트의 배열은 일반적인 배열의 동작을 흉내 낸 특수한 객체다.**
- 자바스크립트 배열은 인덱스를 나타내는 문자열을 프로퍼티 키로 가지며, length 프로퍼티를 갖는다. 자바스크립트 배열의 요소는 사실 프로퍼티 value이다.

    ```jsx
    console.log(Object.getOwnPropertyDescriptors([1, 2, 3]));
    /*
    {
      '0': {value: 1, writable: true, enumerable: true, configurable: true}
      '1': {value: 2, writable: true, enumerable: true, configurable: true}
      '2': {value: 3, writable: true, enumerable: true, configurable: true}
      length: {value: 3, writable: true, enumerable: false, configurable: false}
    }
    */
    ```

- 자바스크립트 배열은 **해시 테이블로 구현된 객체**
    - 인덱스로 요소에 접근하는 경우 일반적인 배열보다 성능적인 면에서 느리다. 
    👉 이런 구조적인 단점을 보완하기 위해 대부분의 모던 자바스크립트 엔진은 배열을 일반 객체와 구별하여 좀 더 배열처럼 동작하도록 최적화하여 구현했다.
    - 특정 요소를 삽입, 삭제하는 경우에는 일반적인 배열보다 빠르다.

## 3. length 프로퍼티와 희소 배열

- 자바스크립트의 배열 요소가 연속적으로 이어져있지 않을 수 있다는 (희소 배열) 의미는 다음과 같은 경우를 뜻하는 것이다.

    ```jsx
    const sparse [, 2, , 4];
    console.log(sparse.length); // 4
    console.log(sparse); // [empty, 2, empty, 4]

    // 배열 sparse에는 인덱스가 0, 2인 요소가 존재하지 않는다.
    console.log(Object.getOwnPropertyDescriptors(sparse));
    /*
    {
      '1': { value: 2, writable: true, enumerable: true, configurable: true },
      '3': { value: 4, writable: true, enumerable: true, configurable: true },
      length: { value: 4, writable: true, enumerable: false, configurable: false }
    }
    */
    ```

## 값 없이 비어 있는 요소를 위해 메모리 공간을 확보하지 않으며 빈 요소를 생성하지도 않는다. - 그럼 메모리 상에 어떻게 되어있는 거지..?

- 자바스크립트는 문법적으로 희소 배열을 허용하지만 희소 배열은 사용하지 않는 것이 좋다. 의도적으로 희소 배열을 만들어야 하는 상황은 발생하지 않는다.
- 최적화가 잘 되어 있는 모던 자바스크립트 엔진은 요소의 타입이 일치하는 배열을 생성할 때 일반적인 의미의 배열처럼 연속된 메모리 공간을 확보하는 것으로 알려져 있다.

## 4. 배열 생성

### 4-1. 배열 리터럴

- 배열 리터럴에 요소를 생략하면 희소 배열이 생성된다.
- 배열 리터럴은 객체 리터럴과 달리 프로퍼티 키가 없고 값(value)만 존재한다.

### 4-2. Array 생성자 함수

- Array 생성자 함수는 new 연산자와 호출하지 않더라도, 즉 일반 함수로써 호출해도 배열을 생성하는 생성자 함수로 동작한다. 이는 Array 생성자 함수 내부에서 `new.target`을 확인하기 때문이다. (17.2.7절 참고)

    `remind` `new.target`은 constructor인 모든 함수 내부에서 암묵적인 지역 변수처럼 사용되며, 메타 프로퍼티라고 부른다. new 연산자와 함께 호출되었는지 확인할 수 있는 프로퍼티이다.
    ✔️ new 연산자와 함께 호출되면 함수 내부의 `new.target`은 함수 자신을 가리킴
    ✔️ new 연산자 없이 일반 함수로써 호출되면 함수 내부의 `new.target`은 undefined

- 전달된 인수의 개수에 따라 다르게 동작
    - 전달된 인수가 1개이고 숫자인 경우: length 프로퍼티 값이 인수인 배열 생성 (전부 다 empty)
    - 전달된 인수가 없는 경우: 빈 배열 생성. 즉 배열 리터럴 `[]` 과 같다.
    - 전달된 인수가 2개 이상이거나 숫자가 아닌 경우: 인수를 요소로 갖는 배열을 생성

### 4-3. Array.of

- ES6에서 도입
- 전달된 인수를 요소로 갖는 배열을 생성
- Array 생성자 함수와 다르게, 전달된 인수가 1개이고 숫자인 경우에도 인수를 요소로 갖는 배열을 생성

### 4-4. Array.from

- ES6에서 도입
- 유사 배열 객체 또는 이터러블 객체를 인수로 전달받아 배열로 변환하여 반환

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7425382-6341-4088-a906-96c6b82cee7c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7425382-6341-4088-a906-96c6b82cee7c/Untitled.png)

- 유사 배열 객체와 배열의 모양이 완전히 똑같은데 무슨 차이인가 싶었다. 속을 들여다보니 배열의 프로토타입은 `Array.prototype`, 유사 배열 객체의 프로토타입은 `Object.prototype`

## 5. 배열 요소의 참조

- 배열은 사실 인덱스를 나타내는 문자열을 프로퍼티 키로 갖는 객체.
- 객체에서 존재하지 않는 프로퍼티 키로 접근했을 때 undefined를 반환하는 것처럼 배열도 마찬가지. 희소 배열의 존재하지 않는 요소를 참조해도 마찬가지로 undefined

## 6. 배열 요소의 추가와 갱신

- 객체에 프로퍼티를 동적으로 추가할 수 있는 것처럼 배열도 가능. 존재하지 않는 인덱스를 사용해 값을 할당하면 됨. 이 때 length 프로퍼티 값은 자동으로 갱신된다.
- 현재 배열의 length 프로퍼티 값보다 큰 인덱스로 새로운 요소를 추가하면 희소 배열이 된다. length도 맞춰서 늘어난다.
- 정수 이외의 값을 인덱스처럼 사용하면 프로퍼티가 생성된다. 이 때 추가된 프로퍼티는 length 값에 영향을 주지 않는다.

## 7. 배열 요소의 삭제

- 배열은 사실 객체이기 때문에 delete 연산자를 사용할 수 있다.
- 이 때 length 프로퍼티에 영향을 주지 않고, 희소 배열이 된다.
- 그러니까 사용하지 않는 것이 좋다.
- `Array.prototype.splice` 메서드를 사용하자.

## 8. 배열 메서드

### Array.prototype.push

- push 메서드도 반환값이 있었다. 변경된 length 프로퍼티 값을 반환한다.
- push 메서드는 성능 면에서 좋지 않다. *(헉??!!!)*
- 마지막 요소로 추가할 요소가 하나뿐이라면 length 프로퍼티를 사용하여 직접 추가하는 것이 push 메서드보다 빠르다.

    ```jsx
    const arr = [1, 2];

    // arr.push(3)과 동일한 처리를 한다. 이 방법이 push 메서드보다 빠르다.
    arr[arr.length] = 3;
    console.log(arr); // [1, 2, 3]
    ```

- push, pop, 생성자 함수 또는 클래스를 이용하여 스택 자료구조를 구현할 수 있다.
- shift, unshift, 생성자 함수 또는 클래스를 이용하여 큐 자료구조를 구현할 수 있다.

### Array.prototype.concat

- push, unshift 메서드는 concat 메서드로 대체할 수 있다.
- push, unshift 메서드와 달리 concat 메서드는 새로운 배열을 반환한다.
- concat 메서드는 ES6의 스프레드 문법으로 대체할 수 있다.
- 결론!! 스프레드 문법이 최고다. *(??)*

### Array.prototype.splice

- 원본 배열의 중간에 요소를 추가하거나 제거하는 경우에 사용
- 원본 배열을 직접 변경한다.

### Array.prototype.slice

- slice 메서드가 복사본을 생성하는 것을 이용하여 유사 배열 객체를 배열로 변환할 수 있다.

    ## 동작이 잘 이해가 안됨!!!!!!!

    ```jsx
    function sum() {
      // 유사 배열 객체를 배열로 변환(ES5)
      var arr = Array.prototype.slice.call(arguments);
      console.log(arr); // [1, 2, 3]

      return arr.reduce(function (pre, cur) {
        return pre + cur;
      }, 0);
    }

    console.log(sum(1, 2, 3)); // 6
    ```

- 이터러블 객체는 스프레드 문법을 사용하여 간단하게 배열로 변환할 수 있다.

## 9. 배열 고차 함수

- 고차 함수는 함수를 인수로 전달받거나 함수를 반환하는 함수를 말한다.
- 고차 함수는 함수형 프로그래밍에 기반을 두고 있다.

### Array.prototype.sort

- sort 메서드는 배열의 요소를 일시적으로 문자열로 변환한 후 정렬한다.
- 원본 배열을 직접 변경한다.
- 숫자 요소를 정렬할 때는 sort 메서드에 정렬 순서를 정의하는 비교 함수를 인수로 전달해야 한다.
    - 비교 함수는 양수, 음수, 또는 0을 반환해야 한다. (반환값이 0인 경우의 정렬 방식은 ECMAScript 사양에 명시되어 있지 않아서 자바스크립트 엔진마다 동작이 다를 수 있다.)
    - 반환값이 음수: 첫 번째 인수를 우선하여 정렬
    - 반환값이 양수: 두 번째 인수를 우선하여 정렬
    - 반환값이 0: 정렬하지 않음

**sort 메서드의 정렬 알고리즘**
quicksort 알고리즘을 사용하다가 ES10에서 timsort 알고리즘을 사용하도록 바뀌었다.
퀵소트 알고리즘은 동일한 값의 요소가 중복되어 있을 때 초기 순서와 변경될 수 있는 불안정한 정렬 알고리즘으로 알려져 있다.

## 단순한 숫자 말고 객체의 특정 프로퍼티를 정렬하는 건 아직도 어렵다...

### Array.prototype.forEach

- 폴리필을 살펴보면, forEach 또한 for문으로 구현되어 있다는 것을 알 수 있다. call 메서드를 통해 thisArg를 전달하면서 콜백함수를 호출한다.
- for문에 비해 성능이 좋지는 않다.

### Array.prototype.reduce

**reduce 메서드의 다양한 활용법 (익숙하지 않은 것들 정리)**

- 요소의 중복 횟수 구하기 (객체 활용)
- 중첩 배열 평탄화 (flat 메서드 사용하는 게 더 직관적)
- 중복 요소 제거 (filter 메서드 사용하는 게 더 직관적, Set 사용도 좋음)
- 배열의 모든 고차 함수는 reduce로 구현 가능
- 초기값은 옵션이지만 초기값을 전달하는 것이 안전하다.

### Array.prototype.flatMap

- map 메서드를 통해 생성된 새로운 배열을 평탄화한다.
- map 메서드와 flat 메서드를 순차적으로 실행하는 효과
- 그러나.. 1단계만 평탄화할 수 있다. 그 이상 중첩되었다면 map, flat을 각각 호출해야 한다.
