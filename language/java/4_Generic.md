# Generic 이란?

클래스에서 사용하는 객체의 타입을 클래스 내부가 아닌 외부에서 결정하는 것이다. 작성한 코드에 따라 컴파일 시에 객체의 타입이 지정된다. 

Generic 을 사용하면 다음과 같은 장점이 있다.

1. 컴파일 시에 타입 체크를 하므로 타입 안정성을 보장한다.
2. 반환값에 대한 형변환 로직이 생략 가능하다.
   - Generic 이 추가되기 전인 JDK 1.5 이전에는 보편적인 객체의 타입에서 `Object` 를 사용하였다. Object 타입으로 사용할 경우 반환값에서 형변한 과정이 필요하다.

### 참고 사이트
- https://st-lab.tistory.com/153
- http://www.tcpschool.com/java/java_generic_concept
