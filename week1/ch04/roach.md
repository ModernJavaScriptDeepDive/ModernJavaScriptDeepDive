# 변수

- 우리가 프로그래밍을 하기 위해서는 무언가를 담고 있는 변수라는 개념이 필요하다. 변수는 간단히 우리의 값을 저장할 수 있는 공간이라고 생각하는 것이 좋다.
아래의 예시를 한번보자

```javascript
10 + 20
```

만약 우리가 컴퓨터라 가정하고, 위의 식을 본다면 첫번째로 아래와 같이 해석할 것이다.

**10 , '+', 20** 이 있고 **10과 20은 숫자이고 + 는 덧셈기호**이다. 그리고 난 뒤 우리는 **우리가 해석**한대로 10 과 20을 더해 30이라는 **숫자를 도출**해 낼 것이다.

좀 더 프로그래밍 답게 들어가면, **자바 스크립트 앤잔**운 저 위의 식을 해석하기 위해서는 **10, '+', 20 이 각각 무슨 의미**인지를 알고 있어야 하며,
**10 + 20 이라는 표현식** 또한 **해석**할 수 있어야 한다.

자바 스크립트는 좌변부터 계산을 시작하므로, 우리가 엔진이 되었다 생각하고 계산해보자!

먼져 좌 우변의 숫자 값 피연산자를 메모리 저장공간에 저장한다. 그리고 연산은 CPU 에서 이뤄지므로, 해당 피연산자의 값과 연산 기호를 CPU 에서 해석하여 연산이 이뤄진다. 연산 결과로 이루어진 값 30도 메모리 주소 어딘가에 저장된다.

C 언어 였다면 메모리 주소로 접근하는 것이 가능하지만, **대부분의 언어들은 메모리 접근을 권하지 않는다**. 따라서 자바스크립트 또한 그렇다.

그래서 우리가 계산한 값 30에 도달하기 위해서는 **우리는 어떤 변수에 30이란 값을 담아줘야 할 것**이다.

따라서 위의 식을 아래와 같이 변경해보자

```javascript
const x = 10 + 20

console.log(x)
```

우리는 이제 30 이라는 값을 출력할 수 있게 되었다. 

어떻게 보면 변수란 값을 담아주는 것이 아닌, 해당 **메모리 주소를 가르키고 있는 하나의 암호화 된 수단**일 수도 있다.

따라서 우리는 앞으로 변수를 단순히 값을 저장하는 것이 아닌, **해당 메모리 주소를 식별하는 하나의 이름**으로서 인지하여야 한다.

우리는 이러한 변수를 통한 식별 시스템으로 인해, **쉽게 값을 재사용**하고, **쉽게 메모리 공간에 값을 적재**하는 것이 가능해졌다.

## 호이스팅

- JavaScript 에는 호이스팅이란 재미있는 개념이 하나 있다. 아래의 코드 예시를 한번 보자

```javascript
console.log(roach)

var roach
```

위의 코드는 Java 였다면, undefined filed 머시기 하면서 오류가 날거 같지만.. 자바 스크립트는 나지 않는다. **정확하게는 undefined 가 출력**된다.
근데 자바 스크립트는 런타임에 하나하나씩 읽으면 어떻게 저게 초기화가 되어있을까...? 앞에서 봤듯이, 초기화 과정을 거쳐야만 undefined 로 할당이 되는데..
그 이유는 JavaScript 엔진이 런타임에서 코드를 한줄 한줄씩 순차적으로 인터프리팅 하기 전에 **평가 과정**을 거치면서, 소스코드를 실행시킬 준비를 하기 때문이다..
즉 위에서 말했듯 10 + 20 이라느 식이 있을때 10, '+', 20 이 뭔지 알아야 실행시키므로 이런 **평가 과정**에서 초기화를 거치는 것이다.

즉 따라서 이렇게 평가를 먼져하는 것이지만, 한줄한줄씩 읽는다고 했을때는 **변수의 선언이 마치 위로 끌어올려지는 것처럼 보이기에** 이 현상을 **호이스팅**이라고 한다.