## **캐시, 검증헤더와 조건부 요청**  
* 캐시 미적용  
  * 데이터가 변경되지 않아도 계속 네트워크를 통해서 데이터를 다운해야함  
  * 브라우저 로딩 속도가 느림  

* 캐시 적용  
  * 캐시 가능 시간동안 네트워크를 사용하지 않아도 됨  
  * 브라우저 로딩 속도가 매우 빠름  

* If-Modified-Since, Last-Modified (캐시에 저장된 날짜와 서버 날짜 비교)  
  * 조건 만족시 200 OK, 헤더 데이터(0.1M) + BODY(1.0M), 전송 용량 1.1M  
  * 조건 불만족시 304 Not Modified(변경이 없음), 헤더 데이터만 전송, 전송 용량 0.1M  

* 단점  
  * 1초 미만 단위로 캐시 조정 불가능  
  * 날짜 기반의 로직 사용  
  * 데이터를 수정해서 날짜는 다르지만, 같은 데이터를 수정해 데이터 결과가 똑같은 경우  
  * 서버에서 별도의 캐시 로직을 관리하고 싶은 경우(큰 영향 없는 변경에서 유지하고 싶은 경우)  

* ETag, If-None-Mactch (캐시용 데이터에 임의의 고유한 버전 이름을 달아둠)  
  * 데이터 변경시 이름 변경  
  * ETag만 보내서 같으면 유지, 다르면 다시 받기  
  * 캐시 제어 로직을 서버에서 완전히 관리  

</br>

## **캐시 제어 헤더**  
* Cache-Control : max-age - 캐시 유효 시간, 초 단위  
* Cache-Control : no-cache - 데이터는 캐시해도 되지만, 항상 원 서버에 검증 후 사용  
* Cache-Control : no-store - 데이터에 민감한 정보가 있으므로 저장하면 안됨  
* Pragma : no-cache - HTTP 1.0 하위 호환  
* Expires : 날짜 - 케시 만료일 지정(하위 호환), Cache-Control : max-age 사용 권장 같이 사용시 Expires 무시  

</br>

## **프록시 캐시**
* Cache-Control: public - 응답이 public 캐시에 저장되어도 됨  
* Cache-Control: private - 응답이 해당 사용자만을 위한 것임, private 캐시에 저장해야 함(기본값)   
* Cache-Control: s-maxage - 프록시 캐시에만 적용되는 max-age  
* Age: 60 (HTTP 헤더) - 오리진 서버에서 응답 후 프록시 캐시 내에 머문 시간(초)  

</br>

## **캐시 무효화**
* 확실한 캐시 무효화 응답  
  * Cache-Control: no-cache, no-store, must-revalidate, Pragma: no-cache  
 
* no-cache + ETag - 프록시 캐시 거쳐 원 서버에 요청  
  * 원 서버 접근 불가시 프록시 캐시에서라도 오래된 데이터 보여줌  

* must-revalidate  
  * 원 서버 접근 불가시 항상 오류(504 Gateway Timeout)
</br>  

## **정리** 
* 쿠키는 서버의 필요에 의해 클라이언트에 저장하는 데이터  
* 캐시는 클라이언트 자체에서 페이지 로드를 효율적으로 하려고 저장하는 데이터  
* ETag는 고유 이름, Last-Modified는 날짜로 캐시 저장  
* 데이터 변경 - 참(200 OK) 데이터 미변경 - 거짓(304 Not Modified)  

</br>

출처 : 인프런 - 모든 개발자를 위한 HTTP 웹 기본 지식
