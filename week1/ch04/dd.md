# 변수

## 변수, 식별자, 키워드, 예약어 

- 변수 : 하나의 값을 저장하기 위해 확보한 메모리 공간 그 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름

- 식별자 : 어떤 값을 구별해서 식별할 수 있는 고유한 이름. 프로그램에서 **엔티티에 부여된 이름**

- 키워드 : 자바스크립트 엔진이 수행할 동작을 규정한 일종의 명렁어. 

- 예약어 : 해당 언어에서 이미 사용하기로 예약한 단어이다. 키워드와 거의 동일시되긴 하지만, 엄밀히 말하면 다르다. 예약어에 등록된 단어는 개발자가 **식별자로 사용할 수 없다** 

### 변수 vs 식별자

- 변수는 메모리 공간 그 자체이며, 변수의 이름(변수명)은 식별자이다.

## 호이스팅

- 변수 선언은 소스코드가 한 줄씩 순차적으로 실행되는 시점, 런타임이 아니라 **그 이전 단계(평가)**에서 먼저 실행된다.

- 호이스팅에 대한 자료들이 주로 선언부가 코드 상단으로 옮겨지는 것처럼 언급하곤 하는데, 이는 엄밀히 말하면 잘못된 설명이다.

- 코드의 위치가 변하는게 아니라, 선언부는 **컴파일 단계에서 실행**되어 **메모리를 할당 받고 저장되기에** 위로 끌어올려지는 것 처럼 보이는 것뿐이다. 

- 단 값의 할당은 런타임에 실행된다.

### 컴파일? 자바스크립트는 컴파일 단계가 없는 인터프리터 언어 아닌가?


- JS가 인터프리터 언어라는 공식 명세는 존재하지 않는다.

- V8 엔진은 js 코드를 인터프리터 방식으로 컴파일 하고, 이를 ByteCode로 만든다.  


- 나머지는 [V8에서 Javascript 코드를 실행하는 방법 정리해보기](https://pks2974.medium.com/v8-%EC%97%90%EC%84%9C-javascript-%EC%BD%94%EB%93%9C%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-%EC%A0%95%EB%A6%AC%ED%95%B4%EB%B3%B4%EA%B8%B0-25837f61f551)를 참고하자

## 재할당

- 해당 변수의 메모리 공간에 재할당 하는 값으로 바꾸는게 아니라 새로운 메모리 공간을 할당 받고, 새로운 값을 저장 한 후 해당 변수명(식별자)와 새로운 메모리 주소를 연결한다. 

- 이후 식별자가 연결되지 않은 메모리 공간은 가비지 콜렉터에 의해 해제된다. 