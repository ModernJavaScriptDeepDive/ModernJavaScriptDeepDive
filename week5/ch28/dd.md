# Number

## 프로퍼티

### Number.EPSILON

> 1과 1보다 큰 수중에서 가장 작은 수와의 차이

- 부동소수점 오차를 해결하기 위해 사용한다

#### 0.1 + 0.2 === 0.3이 false로 나오는 이유(부동소수점 산술 연산)

- 정수는 2진법으로 오차 없이 저장 가능

- 부동소수점은 2진법으로 변환하면 무한소수가 되어 미세한 오차가 발생

### Number.MAX_VALUE / Number.MIN_VALUE

> 자바스크립트에서 표현할 수 있는 가장 큰/작은 양수.

### Number.MAX_SAFE_INTEGER / Number.MIN_SAFE_INTEGER

> 자바스크립트에서 안전하게 표현할 수 있는 가장 큰/작은 정수값

#### 안전하다는게 뭘까?

- 정수를 정확하고 올바르게 비교할 수 있다는 뜻이다.

- JavaScript가 IEEE 754에 기술된 배정밀도 **부동소숫점 형식 숫자체계**를 사용하기 때문

- `Number.MAX_SAFE_INTEGER + 1 === Number.MAX_SAFE_INTEGER + 2`는 `true`로 평가된다.

### Number.POSITIVE_INFINITY / Number.NEGATIVE_INFINITY

> 양/음 무한대

<br/>
<hr/>
<br/>

## 메소드

Number의 메소드는 기본적으로 입력값에 대해 암묵적 타입 변환을 하지 않는다.

### Number.isFinite()

> 입력값이 무한인지 판별.

### Number.isInteger()

> 입력값이 정수인지 판별

### Number.isNaN()

> 입력값이 NaN인지 판별

### Number.toFixed

> 숫자를 반올림하고 **문자열로 반환**

- 인자로 0~20 자리 까지 반올림하는 소수점 이하값을 지정할 수 있다.

## 숫자 뒤의 .

- 엔진은 기본적으로 **부동소수점 숫자의 소수 구분 기호**로 해석한다

- 따라서 ()로 묶거나, 한 칸 띄어써서 표현하거나, **변수에 저장해서** 사용해야한다
