# 모듈

> 어플리케이션을 구성하는 개별적 요소. 재사용 가능한 코드 조각

- 파일 스코프(모듈 스코프)를 가질 수 있어야한다
- 모듈 내에 존재하는 자산(변수, 함수, 객체 등)은 캡슐화되어 외부에서 접근할 수 없다.
- 단, export를 통해 선택적으로 자산을 외부에 공개할 수 있다.
- export된 모듈의 자산을 다른 모듈에서 사용하는 것을 import라고 한다. 