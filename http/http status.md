## **상태코드**
* 1xx (Informational) : 요청이 수신되어 처리중  
* 2xx (Successful) : 요청 정상 처리  
* 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요  
* 4xx (Client Error) : 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음  
* 5xx(Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함

</br>

## **2xx (Successful) - 클라이언트의 요청을 성공적으로 처리**
* 200 OK - 요청성공  
  
* 201 Created - 요청 성공해서 새로운 리소스가 생성됨    

* 202 Accepted - 요청이 접수되었지만 처리가 완료되지 않음    

* 204 No Content - 서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음   
   * 예) 웹 문서 편집기에서 save 버튼

</br>

## **3xx (Redirection) - 요청을 완료하기 위해 유저 에이전트의 추가 조치 필요**
* 리다이렉션  
  * 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동  

* 영구 리다이렉션 - 301, 308
  * 리소스의 URI가 영구적으로 이동
  * 원래의 URL를 사용X, 검색 엔진 등에서도 변경 인지  
  * 301 Moved Permanently - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문 제거될 수 있음  
  * 308 Permanent Redirect - 301과 기능 같음, 리다이렉트시 요청 메서드와 본문 유지(처음 POST를 보내면 리다이렉트도 유지)  

* 일시적인 리다이렉션 - 302, 307, 303  
  * 리소스의 URI가 일시적으로 변경  
  * 검색 엔진 등에서 URL을변경하면 안됨  
  * 302 Found - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문 제거될 수 있음  
  * 307 Temporary Redirect - 302와 기능 같음, 리다이렉트시 요청 메서드와 본문 유지  
  * 302 See Other  - 302와 기능 같음, 리다이렉트시 요청 메서드가 GET으로 변경  

* PRG : Post/Redirect/Get (일시적인 리다이렉션 예시) 
  * POST로 주문 후에 새로 고침으로 인한 중복 주문 방지  
  * 주문 후 결과 화면을 GET 메서드로 리다이렉트  
  * 새로고침해도 결과 하면을 GET으로 조회  

## **4xx (Client Error) 클라이언트 오류** 
* 400 Bad Request - 클라이언트가 잘못된 요청을 해서 서버가 요청을 처리할 수 없음  
  * 요청 구문, 메시지 등등 오류  
  * 클라이언트는 요청 내용을 다시 검토, 전송해야함  
  * 예) 요청 파라미터가 잘못되거나, API 스펙이 맞지 않을 때  

* 401 Unauthorized - 클라이언트가 해당 리소스에 대한 인증이 필요함  
  * 인증 되지 않음  
  * 401 오류 발생시 응답에 WWW-Authenticate 헤더와 함께 인증 방법을 설명  

* 403 Forbidden - 서버가 요청을 이해했지만 승인을 거부함  
  * 주로 인증 자격 증명은 있지만, 접근 권한이 불충분한 경우  
  * 예) 어드민 등급이 아닌 사용자가 로그인은 했지만, 어드민 등급의 리소스에 접근하는 경우  

* 404 Not Found - 요청 리소스를 찾을 수 없음  
  * 요청 리소스가 서버에 없음  
  * 또는 클라이언트가 권한이 부족한 리소스에 접근할 때 해당 리소스를 숨기고 싶을 때  

## **5xx (Server Error) 서버 오류**
* 500 Internal Server Error - 서버 문제로 오류 발생, 애매하면 500 오류  
  * 서버 내부 문제로 오류 발생  
  * 애매하면 500 오류  

* 503 Service Unavailabe - 서비스 이용 불가  
  * 서버가 일시적인 과부하 또는 예정된 작업으로 잠시 요청을 처리할 수 없음  
  * Retry-After 헤더 필드로 얼마뒤에 복귀되는지 보낼 수도 있음

## **정리**
* 4xx는 클라이언트 오류, 5xx는 서버 오류  
* 3xx는 크게 영구 리다이렉션, 일시적인 리다이렉션 두 가지로 나뉨
* 실무에서 308보다 301를 쓴다 (URL가 바뀌면 내부적으로 데이터가 변경되기 때문)  
* 503보는 경우는 드물다 (장애는 예고하고 나지 않기 때문)  

</br>

출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
