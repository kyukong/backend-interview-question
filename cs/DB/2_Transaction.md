# Transaction

트랜잭션이란, 데이터베이스 상태를 변환시키는 하나의 논리적 기능 수행 단위이다. 즉, 한번에 수행되어야 할 일련의 연산이다.

## 롤백과 커밋

### 롤백(Rollback)
하나의 트랜잭션 처리가 비정상적으로 종료되면 트랜잭션의 원자성을 위해 해당 트랜잭션에서 작업한 모든 연산을 취소하여 데이터베이스에 반영하지 않는다. 롤백하고 난 후에는 해당 트랜잭션을 재시작하거나 폐기해야 한다.

### 커밋(Commit)
하나의 트랜잭션 작업이 정상적으로 끝마쳤을 때 커밋을 한다. 커밋을 해야 데이터베이스에 변경사항이 반영된다. 하나의 트랜잭션이 정상적으로 끝났다는 것을 알려주는 연산이다.

## 트랜잭션의 상태
- Active(활동 상태) : 연산이 수행중인 상태
- Partially Committed(부분 완료 상태) : 마지막 연산이 실행된 직후의 상태. 연산은 모두 처리했지만 데이터베이스에는 반영되지 않음
- Committed(완료 상태) : 트랜잭션이 성공적으로 완료되어 Commit 을 한 상태
- Failed(실패 상태) : 장애가 발생하여 트랜잭션이 중단된 상태
- Aborted(철회 상태) : 수행에 실패하여 Rollback 연산을 실행한 상태

### 참고 사이트
- https://tecoble.techcourse.co.kr/post/2021-07-11-database-transaction/