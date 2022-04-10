## **HTTP 응답 - HTTP API, 메시지 바디에 직접 입력**
![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162619365-3fc880e5-df58-439f-8061-4db48b384845.png)

* V1 : HttpServletResponse 객체를 통해 직접 응답 메시지 전달  
* V2 : ResponseEntity를 통해 전달, HTTP 응답 코드도 설정 가능  
* V3 : @ResponseBody를 사용해 view를 사용하지 않고, HTTP 메시지 컨버터를 통해 메시지를 직접 입력 ResponseEntity도 동일한 방식  
* JsonV1 : ResponseEntity를 반환, HTTP 메시지 컨버터를 통해 JSON 형식으로 변환되어 반환  
* JsonV2 : @ResponseStatus(HttpStatus.OK)애노태이션을 사용해 응답 코드 설정 가능  
  * 애노테이션을 사용하면 응답 코드를 동적으로 변경할 수 없음 동적 변경은 ResponseEntity 사용  

## **@RestController**  
* @Controller + @ResponseBody 형식임  
* Rest API를 만들 때 사용하는 컨트롤러  

## **정리**  
* 응답 코드 동적 변경 필요시 ResponseEntity 그 외 @ResponseStatus  
* @Rest API 만들 땐 @RestController를 사용하자  

</br>

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
