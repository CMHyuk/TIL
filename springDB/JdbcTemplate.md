## JdbcTemplate
* 템플릿 콜백 패턴을 사용해 JDBC를 사용할 때 발생하는 대부분의 반복 작업 처리  
* 반복 작업  
  * 커넥션 획득  
  * statement 를 준비하고 실행  
  * 결과를 반복하도록 루프를 실행  
  * 커넥션 종료, statement , resultset 종료  
  * 트랜잭션 다루기 위한 커넥션 동기화  
  * 예외 발생시 스프링 예외 변환기 실행   


* 동적 SQL을 해결하기 어려움  

```template.update()``` : 데이터 변경  
```template.queryForObject()``` : 데이터 하나 조회  
```template.query()``` : 데이터를 리스트로 조회  

```NamedParameterJdbcTemplate``` : 파라미터 순서 신경 안 쓰고 바인딩  
* SQL에서 ? 대신 :파라미터 이름  

## 파라미터 바인딩  
* MAP  
* SqlParameterSource : MapSqlParameterSource, BeanPropertySqlParameterSource 
```BeanPropertySqlParameterSource``` : 자바빈 프로퍼티 규약을 통해 자동으로 파라미터 객체 생성  
```MapSqlParameterSource```은 Dto에 없는 값을 바인딩 할때 사용

# 카멜 표기법  
```select member_name as username```와 같이 칼럼과 객체 이름 다를 때 별칭 사용
```select item_name```으로 조회해도 ```setItemName()```에 값 들어감  
컬럼 이름과 객체 이름이 완전히 다른 경우에만 별칭 사용  

</br>  

출처 : 스프링 DB 2편 - 데이터 접근 핵심 원리







