# 전역 변수의 문제점

## 컴파일은 전역변수 선언문만 실행한다.

> 호이스팅은 스코프 단위로 동작한다.

런타임 전 컴파일 시 선언문을 먼저 실행하는 컴파일 단계가 있지만, 이건 전역 변수 한정이다.

함수 내에 있는 지역 변수는 컴파일 타임이 아니라 함수가 실행되는 런타임에, 함수 내부가 한 줄씩 읽히기 전에 JS 엔진에 의해 먼저 실행된다.

즉, 함수의 작은 블록 안에서도 선언문을 먼저 실행한 후 한 줄씩 읽는다. (타임은 런타임이다)


## 변수의 생명 주기

- 메모리 공간 확보(allocate)

- 메모리 공간 해제(release)

- 가용 메모리 풀 반환 (memory pool)


## 전역 변수의 단점

### 암묵적 결합

- 모든 코드가 전역 변수를 참조/변경 가능하다


- 코드 가독성 저하, 의도치 않은 변경 가능성 올라감

### 긴 생명 주기

- 전역 변수는 생명 주기가 길어서 메모리 리소스를 오래 소비함.

### 스코프체인 상에서 종점에 존재

- 최상단에 있기에 **검색 속도가 가장 느림**

### 네임스페이스 오염

- JS의 가장 큰 문제점은 파일이 분리되어 있다해도 하나의 전역 스코프를 공유한다 (script 태그 여러개 )

=> 이문제는 ES Module 적용으로 해결되는 듯

## ES Module

> ES6 모듈은 파일 자체의 독자적인 모듈 스코프를 제공


