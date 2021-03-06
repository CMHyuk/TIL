## **HTTP 메서드 종류**
* GET : 리소스 조회  
* POST : 요청 데이터 처리, 주로 등록에 사용  
* PUT : 리소스를 대체, 해당 리소스가 없으면 생성  
* PATCH : 리소스 부분 변경  
* DELETE : 리소스 삭제

</br>

## **GET**
* 서버에 전달 하고 싶은 데이터는 query(쿼리 파라미터, 쿼리 스트링)를 통해 전달  
* 메시지 바디를 통해 전달할 수 있지만 지원 하지 않는 곳이 많음

</br>

## **POST**
* 요청 데이터 처리  
* 메시지 바디를 통해 서버로 요청 데이터 전달

## **PUT**
* 리소스를 대체(덮어버림)  
* 클라이언트가 리소스를 식별 -> 클라이언트가 URI 지정 <==> POST와 차이점

</br>

## **PATCH**
* 리소스 부분 변경

</br>

## **정리**
* HTTP 메서드로 GET, POST, PUT, PATCH, DELETE가 있음  
* PUT은 리소스를 덮어버림, PATCH는 부분 변경  
* PUT은 클라이언트는 리소스 식별 O POST 식별 X

</br>

출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
