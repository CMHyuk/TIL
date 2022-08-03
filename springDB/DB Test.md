## DB Test  
application.properties에 추가    
``` 
spring.datasource.url=  
spring.datasource.username=
```   

다른 테스트와 격리, 반복 실행을 위해 @Transactional 테스트 클래스에 적용  
-> 각 테스트 끝날 때마다 트랜잭션 강제로 롤백  
-> 커밋 필요시 클래스 또는 메서드에 @Commit 적용 or @Rollback(value = false)  

</br>

메모리 DB는 애플리케이션 종료 시 함께 사라지기 때문에 실행 시점에 테이블 새로 생성해야함  
-> 경로에 맞게 schema.sql 파일로 테이블 생성  

</br>

테스트 쪽 application.properties 주석 처리
```
spring.datasource.url=  
spring.datasource.username=
```
스프링 부트가 임베디드 모드로 접근하는 데이터 소스를 제공  
H2같은 데이터베이스를 띄우지 않고 테스트 가능  

</br>

출처 : 스프링 DB 2편 - 데이터 접근 활용 기술
