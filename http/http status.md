## **상태코드**
* 1xx (Informational) : 요청이 수신되어 처리중  
* 2xx (Successful) : 요청 정상 처리  
* 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요  
* 4xx (Client Error) : 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음  
* 5xx(Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함

</br>

# **2xx (Successful)**
* 200 OK  
요청성공  

* 201 Created  
요청 성공해서 새로운 리소스가 생성됨  

* 202 Accepted  
요청이 접수되었지만 처리가 완료되지 않음  

* 204 No Content  
서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음  
예) 웹 문서 편집기에서 save 버튼

</br>

출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
