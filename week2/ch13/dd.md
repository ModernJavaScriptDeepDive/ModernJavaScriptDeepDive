# 스코프

> 모든 식별자가 가지는, 자신이 선언된 위치에 의해 다른 코드가 식별자 자신을 참조할 수 있는 유효 범위. 즉 식별자가 유효한 범위

## 식별자 결정

> JS 엔진이 이름이 같은 두 개의 변수 중 어떤 변수를 참조해야 할 것인지 결정하는 것. 식별자를 검색하는 규칙

## 스코프 체인

> 스코프가 계층적으로 연결된 것. 실행 컨텍스트의 렉시컬 환경을 단방향으로 연결한 것

- 변수를 참조할 때 JS 엔진은 스코프 체인을 통해 변수를 참조하는 코드에서 시작해서 상위 스코프 방향으로 이동하며 변수를 검색한다.

## 함수 레벨 스코프

- var 키워드로 선언된 변수는 함수 블록을 지역 스코프로 인정한다.

## 렉시컬 스코프

- 함수를 어디서 정의했는지에 따라 함수의 상위 스코프를 결정한다.

