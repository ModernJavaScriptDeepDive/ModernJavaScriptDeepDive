# 📒 35- 스프레드 문법

데이터 집합을 펼쳐 개별 의값들의 목록 생성 

- 이터러블만 가능
- 스프레드값 !== 결과 (변수 할당 불가능 )

## 1) 함수 호출 인수
배열을 펼쳐서 함수 인수로 전달할 때
ex) Math.max와 같은 가변인자 함수 시


#### rest vs spread
**rest 파라미터**: 함수 인자로 전달된 인수 목록을 배열오 전달하기 위해 사용

**스프레드** : 이터러블을 펼쳐 개별 값의 목록으로 전달하기 위해 사용

## 2) 배열 리터럴 요소
**concat** : 배열2개 -> 배열1개
**splice** : 배열 중간에 다른 요소 추가, 제거할때
배열 복사

## 3) 객체 리터렁 프로퍼티
스프레드 프로퍼티를 사용하면 일반 객체를 대상