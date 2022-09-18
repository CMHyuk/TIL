## Page
  
* ```PageRequest.of(페이지, 가져올 개수, 정렬 기준, 정렬 대상)``` : 정렬 기준 정렬 대상은 생략 가능, 페이지 인덱스는 0부터 시작  
* ```.getContent()``` : 위 설정에 따라 값을 가져옴  
* ```.getTotalElements()``` : 전체 값 개수  
* ```..getNumber()``` : 페이지 번호   
* ```.getTotalPages()``` : 전체 페이지 개수  
* ```.isFirst()``` : 첫 페이지 여부  
* ```.hasNext()``` : 다음 페이지 존재 여부   

## Slice  
* 3개 요청 시 4개 가져옴  
* 전체 count 가져오지 않음 count 쿼리 안 날림  
* 더보기 기능에 사용  

## Count
* ```@Query(value = , countQuery = )```로 분리로 불필요한 쿼리문 줄임  

## DTO  
```.map()```으로 변환

</br>

출처 : 실전! 스프링 데이터 JPA
