## **HTTP 헤더**
* 용도  
  * HTTP 전송에 필요한 모든 부가 정보  
  * 예) 메시지 바디의 내용, 크기, 인증, 요청 클라이언트, 서버 정보, 캐시 관리 정보...  
  * 표준 헤더가 너무 많음  
  * 필요시 임의의 헤더 추가 가능  

* RFC723x 변화  
  * 엔티티 -> 표현  
  * Representation = representation Metadata + Representation Data  
  * 표현 = 표현 메타데이터 + 표현 데이터  

* HTTP BODY  
 
  표현 헤더  
  Content-Type: text/html;charset=UTF-8  
  Content-Length: 3423  
  
   표현 데이터, 메시지 본문    
   데이터 유형(html, json)  
   
  * 메시지 본문을 통해 표현 데이터 전달  
  * 메시지 본문 = 페이로드  
  * 표현은 요청이나 응답에서 전달할 실제 데이터  
  * 표현 헤더는 표현 데이터를 해석할 수 있는 정보 제공 

## **표현**    
* 표현 헤더는 전송, 응답 둘다 사용  

* Content-Type - 표현 데이터의 형식
  * 미디어 타입, 문자 인코딩(html, json, image)

* Content-Encoding - 표현 데이터의 압축 방식 
  * 표현 데이터를 압축하기 위해 사용  
  * 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가  
  * 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제  
  * 예) gzip, deflate, identity(압축 x)  

* Content-Language - 표현 데이터의 자연 언어
  * 예)ko, en, en-US  

* Content-Length - 표현 데이터의 길이 
  * 바이트 단위  
  * Transfer-Encoding(전송 코딩)을 사용하면 Content-Length를 사용하면 안됨

## **협상(콘텐츠 네고에이션) - 클라이언트가 선호하는 표현 요청** 
* Accept : 클라이언트가 선호하는 미디어 타입 전달
* Accept-Charset : 클라이언트가 선호하는 문자 인코딩
* Accept-Encoding : 클라이언트가 선호하는 압축 인코딩
* Accept-Language : 클라이언트가 선호하는 자연 언어  

* 우선순위  
  * Quality Values(q) 값 사용  
  * 0~1, 클수록 높은 우선순위  
  * 생략 시 1  
  * 구체적인 것이 우선  
  * 구체적인 것을 기준으로 미디어 타입 지정

## **일반 정보**
* From : 유저 에이전트의 이메일 정보  
* Referer : 이전 웹 페이지 주소  
* User-Agent : 유저 에이전트 애플리케이션 정보 -장애 파악 가능    
* Server : 요청을 처리하는 오리진 서버의 소프트웨어 정보  
* Date : 메시지가 생성된 날짜

## **특별한 정보**  
* Host : 요청한 호스트 정보(도메인)  
  * 하나의 IP 주소에 여러 도메인이 적용되어 있을 때
  * 필수로 사용  

* Location : 페이지 리다이렉션  
* Allow : 허용 가능한 HTTP 메서드  
* Retry-After : 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간

## **인증**  
* Authorization: 클라이언트 인증 정보를 서버에 전달  
* WWW-Authenticate: 리소스 접근시 필요한 인증 방법 정의

## **쿠키**
* Set-Cookie: 서버에서 클라이언트로 쿠키 전달(응답)  
* Cookie: 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달
* 생명주기  
  * expires = Sat, 26-Dec-2020 04:39:21 GMT (만료일이 되면 쿠키 삭제)  
  * max-age=3600 (3600초) (0이나 음수를 지정하면 쿠키 삭제)  
  * 세션 쿠키 : 만료 날짜 생략시 브라우저 종료시 삭제  
  * 영속 쿠키 : 만료 날짜 입력시 해달 날짜까지 유지  

* 도메인, 경로를 지정해 접근 권한 설정 가능
* 쿠키는 로그인 세션 관리, 광고 정보 트래킹에 주로 사용  
* 보안에 민감한 데이터는 저장 X (주민번호, 신용카드)  

## **정리**
* Transfer-Encoding와 Content-Length 같이 사용 못함  
* 쿠키하면 로그인 세션, 광고 정보 트래킹을 떠올리자 (정보 저장이라고 생각)  
* Host는 필수로 사용하는 것이다 Host로 먼저 찾은 다음 Port 탐색 ex) aaa.com -> 100port  


출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
