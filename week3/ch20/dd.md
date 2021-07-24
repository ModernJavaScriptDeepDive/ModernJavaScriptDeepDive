# strict mode

> 하지만 이것보다는 ESLint 추천

## strict mode가 발생시키는 에러

### 암묵적 전역

var, const, let이 없는 변수 할당문을 자동으로 전역 변수를 생성해서 할당하는 것을 막음

## 변수, 함수, 매개변수 삭제

delete 사용을 막음

## 매개변수 이름 중복

## with문 사용 


## strict mode 적용에 의한 변화

### 일반 함수의 this는 undefined로 바인딩 된다

### 매개변수에 전달된 인수를 재할당해도 arguments에 반영 안 됨