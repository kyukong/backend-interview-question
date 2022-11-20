# UndoLog

데이터가 변경되었을 때 변경되기 전의 데이터(이전 데이터) 를 보관하는 장소로, 롤백 대비용이자 트랜잭션의 격리 수준을 유지하면서 높은 동시성을 제공하는데 사용된다. UndoLog 에는 실제 변경되는 컬럼의 이전 값과 PK 값만 저장된다.

- READ COMMITTED 이상의 격리 수준(+ REPEATABLE READ, SERIALIZABLE) 에서 MVCC 를 보장하기 위해 Undo 영역의 데이터를 이용한다. 커밋이 되기 전에 다른 사용자가 조회했을 때, Undo 영역의 데이터를 반환한다.
- BEGIN 으로 트랜잭션 시작 후 장시간동안 트랜잭션을 종료하지 않으면 Undo 영역이 무한정 커질 수 있다.

### 참고 사이트
- https://rosebud90.tistory.com/entry/InnoDB-Storage-Engine-%ED%8A%B9%EC%84%B1-%EB%B0%8F-%EA%B5%AC%EC%A1%B0
