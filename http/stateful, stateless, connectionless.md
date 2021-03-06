## HTTP
* HTTP 메시지에 모든 것을 전송(HTML, IMAGEM JSON 등등)
* 현재 HTTP/1.1을 가장 많이 사용  
* HTTP/3가 TCP 대신 UDP를 사용하며 성능 개선으로 각광받음

</br>

## 무상태 프로토콜(Stateless)
* 서버가 클라이언트 상태 보존X
* 장점 : 서버 확장성 높음(스케일 아웃)
* 단점 : 클라이언트가 추가 데이터 전송

</br>

## 상태 유지 - Stateful
* 서버가 장애나면 다시 클라이언트로 돌아가 요청해야함(로그인)

</br>

## 무상태 - Stateless
* 서버가 장애나면 이미 요청에 담겨져 있으므로 중계서버가 같은 기능하는 다른 서버로 던짐(로그인 필요없는 화면)  

</br>

## 비 연결성
* HTTP는 기본이 연결 유지 X
* 서버 자원 효율적 관리 가능
* 초 단위 이하의 빠른 시간 응답  

</br>

한계와 극복  
* TCP/IP 연결 새로 맺어야 함
* 수 많은 자원이 함께 다운
-> 지속 연결로 문제 해결

## 정리
* HTTP/1.1를 많이 사용하지만 최근 HTTP/3가 부상
* 무상태는 최대로 상태는 최소한으로 사용하자
* 비 연결성으로 속도 자원 모두 효율적으로 관리 가능

</br>

출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
