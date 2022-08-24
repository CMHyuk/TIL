## JPQL  
* 엔티티와 속성은 대소문자 구분 O 
* JPQL 키워드는 대소문자 구분 X  
* 별칭 필수   
* TypeQuery : 반환 타입이 명확할 때 사용  ```"SELECT m FROM Member m"```  
* Query : 반환 타입이 명확하지 않을 때 사용 ```"SELECT m.username, m.age from Member m"```  
* ```.getResultList();``` : 결과가 하나 이상일 때 반환 없으면 빈 리스트 반환  
* ```.getSingleResult();``` : 결과가 정확히 하나일 때 반환  
  * ```javax.persistence.NoResultException``` : 결과 x  
  * ```javax.persistence.NonUniqueResultException``` : 결과 둘 이상  
  -> SPRING DATA JPA 사용 시 예외 처리 알아서 해줌 null, Optional 반환  
* ```.setParameter("username", username);``` : 파라미터 바인딩 이름 기준  
* ```.setParameter(1, usernameParam);``` : 위치 기준  
* 파라미터 바인딩은 이름 기준으로 사용하자  

## 프로젝션  
* SELECT절에 조회할 대상을 지정하는 것  
* ```SELECT m FROM Member m``` : 엔티티 프로젝션(영속성 컨텍스트에 의해 관리됨)  
* ```SELECT m.team FROM Member m``` : 엔티티 프로젝션  
* ```SELECT m.address FROM Member m``` : 임베디드 타입 프로젝션   
* ```SELECT m.username, m.age FROM Member m``` : 스칼라 타입 프로젝션  
* 여러 값 조회  
  * new 명령어로 조회  
  * 단순 값을 DTO로 바로 조회  
  * ```SELECT new jpabook.jpql.UserDTO(m.username, m.age) FROM Member m``` 
  * 패키지 명을 포함한 전체 클래스 명 입력  
  * 순서와 타입이 일치하는 생성자 필요  

## 페이징  
* ```setFirstResult``` : 조회 시작 위치  
* ```setMaxResults``` : 조회할 데이터 수  
* ```"select m from Member m order by m.name desc"``` : 페이징 쿼리    
  * desc : 역순으로 조회  
  * asc : 순서대로 조회  

</br>

출처 : 자바 ORM 표준 JPA 프로그래밍 - 기본편
 



