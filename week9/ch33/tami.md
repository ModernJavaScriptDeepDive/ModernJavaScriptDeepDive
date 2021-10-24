#  📒33-Symbol
ES6에서 도입된 변경 불가능한 원시 타입의 값

**중복되지 않는 상수 값** 생성하고 기존코드에 **영향을 주지 않는 프로퍼티**를 추가하기 위해 도입


- 함수 호출로만 생성 가능
- 다른 값과 절대 중복되지 않는 유일값
- `new`연산자 사용 안함
- 문자 or 숫자로 변환되지 않음
- boolean 변환 가능

#### Symbol.for
전역 심벌 레지스트리에서 인수를 키로 사용하는 심벌 값 탐색 (없으면 생성후 반환)

```javascript=
const s1 = Symbol.for('mySymbol')
```

## 🤔 그럼 언제 쓸 수 있을까?

### 1) 상수 객체 생성

상수 이름 자체에 의미가 있는 객체 생성 시 
```javascript=
const color ={
    Red: Symbol('red'),
    Yellow: Symbol('yellow')
}
```

### enum
상수의 열거형 집합 
C,Java,TypeScript에선 지원하지만 JS에서는 지원하지 않음

Object 메서드 사용해서 대체

```javascript=
const color = Object.freeze({
    Red: Symbod('red')
})
```

### 2) 프로퍼티 키
유일무이한 심벌값으로 키를 만들면 다른 프로퍼티 키와 충돌하지 않음
```javascript=
const obj = {
    [Symbol.for('ms')]:1
}
```

### 3) 프로퍼티 은닉
Object.keys 등으로 찾기 어려워 프로퍼티 값 은닉 가능

### 4) 표준 빌트인 객체 확장
비추이지만 굳이 한다면, 심벌값으로 프로퍼티 키 생성해야 버전 up 시 충돌 위험 없음


### 이터러블
순회가능한 이터러블은 `Symbol.iterator`를 키로 갖는 메서드 가짐 
