# Transaction Isolation Level

## Isolation Level
- 트랜잭션에서 일관성 없는 데이터를 허용하는 수준

데이터베이스는 ACID 특징과 같이 트랜잭션이 독립적인 수행을 하도록 한다. 트랜잭션이 DB 를 다루는 동안 다른 트랜잭션이 관여하지 못하도록 Locking 을 한다. 하지만 무조건 Locking 을 할 경우 데이터베이스의 성능은 떨어지며, Locking 의 범위를 줄이면 잘못된 연산이 수행될 가능성이 있다. 따라서 최대한 효율적인 Locking 방법을 수립하기 위해 적절한 격리 수준을 설정해야 한다.

### 1. Read Uncommitted (레벨0)
- SELECT 문장이 수행되는 동안 해당 데이터에 Shared Lock 이 걸리지 않는 계층
- 트랜잭션이 처리중이거나, 아직 Commit 되지 않은 데이터를 다른 트랜잭션이 읽는 것을 허용
- 데이터의 일관성을 유지하는 것이 불가능

### 2. Read Committed (레벨1)
- SELECT 문장이 수행되는 동안 해당 데이터에 Shared Lock 이 걸리는 계층
- 트랜잭션이 수행되는 동안 다른 트랜잭션이 접근할 수 없어 대기함
- Commit 이 이루어진 트랜잭션만 조회 가능
- 대부분의 SQL 서버가 default 로 사용

### 3. Repeatable Read (레벨2)
- 트랜잭션이 완료될 때까지 SELECT 문장이 사용하는 모든 데이터에 Shared Lock 이 걸리는 계층
- 트랜잭션이 범위 내에서 조회한 데이터 내용이 항상 동일함을 보장
- 다른 사용자는 트랜잭션 영역에 해당되는 데이터에 대한 **수정이 불가능**
- MySQL 에서 default 로 사용

### 4. Serializable (레벨3)
- 트랜잭션이 완료될 때까지 SELECT 문장이 사용하는 모든 데이터에 Shared Lock 이 걸리는 계층
- 완벽한 읽기 일관성 모드를 제공
- 다른 사용자는 트랜잭션 영역에 해당되는 데이터에 대한 **수정 및 입력 불가능**

## 낮은 단계 격리 수준을 선택할 때 발생하는 현상

### Dirty Read
- 커밋되지 않은 수정중인 데이터를 다른 트랜잭션에서 읽을 수 있도록 허용할 때 발생하는 현상
- 발생 Level : Read Uncommitted

### Non-Repeatable Read
- 한 트랜잭션에서 같은 쿼리를 두 번 수행할 떄 그 사이에 다른 트랜잭션 값을 수정 또는 삭제하면서 두 쿼리의 결과가 상이하게 나타나 일관성이 깨지는 현상
- 발생 Level : Read Committed, Read Uncommitted

### Phantom Read
- 한 트랜잭션 안에서 일정 범위의 레코드를 두 번 이상 읽었을 때, 첫번쨰 쿼리에서 없던 레코드가 두번쨰 쿼리에서 나타나는 현상
- 트랜잭션 도중 새로운 레코드 삽입을 허용하기 때문에 나타나는 현상
- 발생 Level : Repeatable Read, Read Committed, Read Uncommitted

### 참고 사이트
- https://gyoogle.dev/blog/computer-science/data-base/Transaction%20Isolation%20Level.html
