## DataSource
* 자바에선 커넥션을 획득하는 방법을 추상화 하는 인터페이스(javax.sql.DataSource) 제공  
* 핵심 기능 - 조회  
* DBCP2 커넥션 풀, HikariCP 커넥션 풀의 코드를 직접 의존하는 것이 아닌 인터페이스에 의존 가능  
* DriverManager는 DataSource 인터페이스 사용 x -> 변경 시 관련 코드를 모두 고쳐야함  
  * 스프링에선 DriverManagerDataSource 라는 DataSource를 구현한 클래스 제공  
* 설정과 사용을 분리 가능  
  * 설정 - DataSource를 만들고 필요한 속성들을 사용  
  * 사용 - getConnection()만 호출

</br>

## 정리
* 설정과 사용의 분리 가능    

</br>

출처 : 인프런 - 스프링 DB 1편 - 데이터 접근 핵심 원리
