## **HTTP 요청 메시지**
* HTTP message body에 데이터를 직접 담아 요청  
* @RequestParam, @ModelAttribute를 사용할 수 없음  

</br>

## **HTTP 메시지 바디 정보 조회**
* InputStream(Reader) : 내용을 직접 조회  
* OutStream(Writer) : 직접 결과 출력
* HttpEntity : HTTP header, body 정보를 편리하게 조회, 응답에도 사용 가능(상태코드 설정 가능)  
* @RequestBody : 해더가 필요하다면 HttpEntity나 @RequestHeader를 사용하면 됨

</br>

## **요청 파라미터 vs HTTP 메시지 바디**  
* 요청 파라미터를 조회하는 기능 : @RequestParam, @ModelAttribute  
* HTTP 메시지 바디를 직접 조회하는 기능 : @RequestBody  

</br>

## **HTTP 요청 메시지 -JSON**
```private ObjectMapper objectMapper = new ObjectMapper();```  
* HttpServletRequest를 사용해 HTTP 메시지 바디에서 데이터를 읽어와 문자로 변환  
* 문자로 된 JSON 데이터를 Jackson 라이브러리인 objectMapper 를 사용해서 자바 객체로 변환

 ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162580148-c5de16c6-4ecd-4384-836b-085bcb7f38ad.png)  
 
 </br>
 
 * @RequestBody를 사용해 messageBody에 저장  
 
  ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162580179-6cc760cb-6d73-43a2-af22-bd6cfcf969cb.png)  
  
  </br>
  
  * @RequestBody 객체 변환  
  * @RequestBody 생략 불가능 생략시 @ModelAttribute가 적용됨(HTTP 메시지 바디가 아닌 요청파라미터 처리)
  
  ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162580227-76d38250-8ab7-4e42-af75-c6b30d25048e.png)  
  
  </br>
  
  * HttpEntity  
  
  ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162580314-ec4a807c-32e2-4742-9edc-7a7b0faf016d.png)  
  
  </br>
  
  * @ResponseBody 응답의 경우에도 객체를 HTTP 메시지 바디에 직접 넣을 수 있음  
  
  ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162580375-4ac265e7-13a1-4cea-bcba-5d806bbdde21.png)  
  
  </br>  
  
  * @RequestBody 요청 : JSON 요청 -> HTTP 메시지 컨버터 -> 객체  
  * @ResponseBody 응답 : 객체 -> HTTP 메시지 컨버터 -> JSON 응답  

## **정리**  
* 요청 파라미터(@RequestParam, @ModelAttribute)와 HTTP 메시지 바디(@RequestBody)를 구분하자  
* @RequestParam, @ModelAttribute은 생략 가능하지만, @RequestBody는 생략 불가능  

</br>

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술



