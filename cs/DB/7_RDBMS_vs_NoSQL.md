# RDBMS vs NoSQL

## RDBMS (관계형 데이터베이스)
- DBMS (DataBase Management System) : 데이터베이스를 관리(저장, 조회 등) 해주는 소프트웨어

**관계형** 데이터베이스는 데이터가 하나 이상의 열과 행의 테이블(또는 관계)에 저장되어 서로 다른 데이터 구조가 어떻게 관련되어 있는지 쉽게 파악하고 이해할 수 있도록 사전 정의된 관계로 데이터를 구성하는 정보 모음이다. 관계는 이러한 테이블 간의 상호작용을 기반으로 설정되는 여러 테이블 간의 논리적 연결이다. RDB 에는 외래키를 사용하여 테이블을 `JOIN` 하여 정보 간 관계 또는 링크를 설정할 수 있는 기능이 있어, 여러 데이터 포인트 간의 관계를 쉽게 이해하고 정보를 얻을 수 있다.

관계형 데이터베이스 모델의 장점은 직관적인 데이터 표현 방법을 제공하고, 관련 데이터 포인트에 쉽게 접근할 수 있다는 점이다. 그래서 인벤토리 추적부터 트랜잭션 데이터 처리 및 애플리케이션 로깅까지 **대량의 구조화된 데이터를 관리**해야 하는 조직에서 가장 많이 사용한다.

### 장점
- 정해진 스키마에 따라 데이터를 저장하여 명확한 데이터 구조를 보장한다.

### 단점
- 테이블 사이에 관계를 맺고 있어 시스템이 커질 경우 JOIN 문이 복잡해질 수 있다.
- 성능 향상을 위해서는 Scale-Up(수직적 확장) 만을 지원한다.
  - 비용이 기하급수적으로 늘어날 수 있다.
- 스키마로 인해 데이터가 유연하지 못하다.
  - 스키마 변경이 어렵다.

=> 데이터 구조가 명확하며 변경될 여지가 적은 경우에 사용하는 것이 적합하다. 또한 중복된 데이터가 없어(무결성 보장) 변경이 용이하기 때문에 관계를 맺고 있는 데이터가 자주 변경이 이루어지는 시스템에 적합하다.

## NoSQL (Not Only SQL)

RDB 형태의 관계형 데이터베이스가 아닌 다른 형태의 데이터 저장 기술을 의미한다. RDB 처럼 테이블 간의 관계를 설정하지 않아 테이블은 그저 하나의 테이블일 뿐 `JOIN` 이 불가능하다.

빅데이터의 등장으로 데이터와 트래픽이 기하급수적으로 증가하여 여러 테이블을 묶어 관리하는 관계형 데이터베이스로는 성능이 많이 떨어지게 되었다. 이러한 상황에서 성능을 높이기 위해 NoSQL 을 사용할 수 있다. Scale-Out 이 어려운 RDBMS 와는 달리 NoSQL 은 Scale-Out(수평적 확장) 을 쉽게 할 수 있다는 장점을 가지고 있다.

1. key-value Database
- key-value 형식의 데이터베이스
- value 에는 어떠한 형태의 값이던 저장할 수 있다. (이미지나 비디오도 가능)
- 응답 속도가 매우 빠르다.
- ex) Redis, Riak, Amazon Dynamo DB 등

2. Document Database
- key-document(value) 형식의 데이터베이스
- value 가 계층형이다.
  - 객체지향에서의 객체와 유사하다.
  - 하나의 객체를 여러 개의 테이블에 나눠 저장할 필요가 없다. (document 에 객체 자체를 저장한다)
- key-value 형식처럼 응답 속도가 빠르다.
- ex) MongoDB, CouthDB 등

3. Wide Column Database

4. Graph Database
- 데이터를 Node, Edge, Property 와 함께 그래프 구조를 사용하여 표현한다.
- 개체와 관계를 그래프 형태로 표현한 것이므로 관계형 모델이라고도 할 수 있다.
- 페이스북이나 트위터 같은 소셜 네트워크에서 적합하고, 연관된 데이터를 추천해주는 추천 엔진이나 패턴 인식 등의 데이터베이스로도 적합하다.

### 장점
- 스키마가 없기 때문에 유연하며 자유로운 데이터 구조를 가질 수 있다.
  - 언제든 저장된 데이터를 조정하고 새로운 필드를 추가할 수 있다.
- 데이터 분산이 용이하며 Scale-Out(수평적 확장)을 지원한다.

### 단점
- 데이터 중복이 발생할 수 있으며, 중복된 데이터가 변경될 경우 모든 컬렉션에서 수정해야 한다.
- 스키마가 존재하지 않기 때문에 데이터 구조를 보장하지 않으며 데이터 구조 결정이 어려울 수 있다.

=> 정확한 데이터 구조를 알 수 없고 데이터가 변경/확장이 될 수 있는 경우에 적합하다. 

### 참고 사이트
- https://cloud.google.com/learn/what-is-a-relational-database?hl=ko
- https://khj93.tistory.com/entry/Database-RDBMS%EC%99%80-NOSQL-%EC%B0%A8%EC%9D%B4%EC%A0%90