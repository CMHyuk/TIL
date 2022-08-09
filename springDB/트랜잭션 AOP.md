## 트랜잭션 AOP  
* AOP를 적용하면 객체 대신에 프록시를 빈으로 등록  
* 내부 호출은 프록시를 거치지 않음  
   *  메서드 앞에 별도의 참조가 없으면 ```this```라는 뜻으로 자신의 인스턴스를 가르킴  
   *  내부에 있는 메서드를 별도의 클래스로 분리  
* public 메서드만 트랜잭션 적용 ```protected , private , package-visible```에는 적용 x  
* ```@PostConstruct```와 ```@Transactional```을 함께 사용하면 트랜잭션 적용 x  
   * 초기화 코드 호출 -> 트랜잭션 AOP 적용  
   * ```@EventListener(value = ApplicationReadyEvent.class)```사용으로 해결  

## 트랜잭션 옵션  
* ```value, transactionManager``` : 트랜잭션 매니저 지정 옵션 보통 생략  
* ```rollbackFor``` : 예외를 지정해 발생 시 롤백  
* ```noRollbackFor``` : ```rollbackFor```와 반대로 예외를 지정해 발생 시 롤백x  
* isolation : 트랜잭션 격리 수준 지정 일반적으로 커밋된 읽기 사용  
   * ```DEFAULT``` : 데이터베이스에서 설정한 격리 수준을 따름  
   * ```READ_UNCOMMITTED``` : 커밋되지 않은 읽기  
   * ```READ_COMMITTED``` : 커밋된 읽기  
   * ```REPEATABLE_READ``` : 반복 가능한 읽기  
   * ```SERIALIZABLE``` : 직렬화 가능  
* timeout : 트랜잭션 수행 시간 지정  
* ```readOnly=true``` : 읽기 전용 트랜잭션 등록, 수정, 삭제 불가 성능 최적화 발생  

## 예외와 트랜잭션 커밋, 롤백
* 체크 예외 -> 커밋 언체크(런타임) 예외 -> 롤백  
* 체크 예외 : 비즈니스 의미가 있을 때 사용(주문 결제 시 잔고 부족)  
* 언체크 예외 : 복구 불가능한 예외

</br>

출처 : 스프링 DB 2편 - 데이터 접근 활용 기술

