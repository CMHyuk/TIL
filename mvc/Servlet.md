## **서블릿** 
```
  @WebServlet(name = "helloServlet", urlPatterns = "/hello") 
public class HelloServlet extends HttpServlet { 
 @Override 
 protected void service(HttpServletRequest request, HttpServletResponse response){ 
 //애플리케이션 로직
 } 
}
```
* urlPatterns(/hello)의 URL이 호출되면 서블릿 코드가 실행  
* HTTP 요청 정보를 편리하게 사용할 수 있는 HttpServletRequest  
* HTTP 응답 정보를 편리하게 제공할 수 있는 HttpServletResponse  
* 개발자는 HTTP 스펙을 매우 편리하게 사용  

</br>  

## **HTTP 요청, 응답 흐름**  
* WAS는 Request, Response 객체 새로 생성 후 서블릿 객체 호출 
* Request 객체에서 HTTP 요청 정보를 꺼내서 사용  
* Response 객체에 HTTP 응답 정보를 입력  
* WAS는 Response 객체에 담겨있는 내용으로 HTTP 응답 정보 생성  

</br>  

## **서블릿 컨테이너**  
* WAS = HTTP 통신 + 서블릿 컨테이너  
* 서블릿 객체는 싱글톤으로 관리  
  * 공유 변수(멤버 변수) 사용 주의  
* JSP도 서블릿으로 변환 되어 사용  
* 동시 요청을 위한 멀티 쓰레드 처리 지원

</br>

## **서블릿 등록**
* ```@ServletComponentScan``` : 서블릿 자동 등록  
* ```@WebServlet(name = "서블릿 이름", urlPatterns = "URL 매핑")  ```
* ```protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException```  : request - HTTP 요청 메시지를 기반으로 생성, response - Response 객체 정보로 HTTP 응답 생성
* ```logging.level.org.apache.coyote.http11=debug``` : HTTP 요청 메시지 로그로 확인하기  

</br>  

## **메서드**  
* ```String username = request.getParameter("username") ``` : 쿼리 파라미터 조회  
* ```response.getWriter().write();``` : HTTP 메시지 바디에 데이터 들어감  

</br>

*  HttpServletRequest(start-line 정보)  
   * ```request.setAttribute(name, value)``` : (HTTP 요청 시작부터 끝날 때까지 유지) 저장  
   * ```request.getAttribute(name)``` : (HTTP 요청 시작부터 끝날 때까지 유지) 조회  
   * ```request.getSession(create: true)``` : 세션 관리 기능(로그인 판별)  
   * ```request.getMethod()``` : HTTP 메서드 조회 
   * ```request.getProtocoal()``` : HTTP 버전 조회
   * ```request.getScheme()``` : 프로토콜 조회 
   * ```request.getRequestURL,URI()``` : URL,URI 조회  
   * ```request.getQueryString()``` : 쿼리 파라미터 조회  
   * ```request.isSecure()``` : HTTPS 판별  

</br> 

* HttpServletRequest(헤더 정보)  
   * ```request.getHeader()``` : 원하는 헤더 조회
   * ```request.getServerName()``` : 호스트 정보 조회  
   * ```request.getServerPort()``` : 포트 조회  
   * ```
     request.getHeaderNames().asIterator().
              forEachRemaining(headerName -> System.out.println("headerName = " + headerName) : 모든 헤더 조회  
     ```
   * ```
     request.getLocales().asIterator().
              forEachRemaining(locale -> System.out.println("locale = " + locale) : 언어 순서 조회  
     ```  
   * ```request.getLocale()``` : 우선순위 언어 조회  
   * ```
     if(request.getCookies() != null) {
         for(Cookie cookie : request.getCookies()) {
             System.out.println(cookie.getName() + ": " + cookie.getValue());
         }
     } : 쿠키 조회
     ```  
   * ```request.getContentType()``` : text 타입 조회(GET은 null 반환)   
   * ```request.getCharacterEncoding()``` : 인코딩 정보 조회
   * ```request.getContentLength()``` : 길이 조회  

</br>

## **HTTP 요청 데이터**  
* GET 쿼리 파라미터  
  *  ```
     request.getParameterNames().asIterator().
              forEachRemaining(paramName -> System.out.println("paramName(key) = " + request.getparameter(paramName)(value))) : 모든 파라미터 조회  
     ```  
  * ```request.getParameter()``` : 단일 파라미터 조회(중복시 첫번 째 값 반환)
  * ```request.getParameterValues()``` : 이름이 같은 복수 파라미터 조회  

</br>

* API 메시지 바디 - 단순 텍스트  
  * ```ServletImputStream inputStream = request.getInputStream();``` : 메시지 바디 내용을 바이트 코드로 얻음  
  * ```StreamUtils.copyToString(inputStream, StandardCharsets.UTF_8)``` : (스프링이 제공)변환 시 인코딩 정보 알려줘야함  

* JSON  
  * JSON 형식으로 파싱할 수 있게 객체 생성(lombok 사용시 getter, setter 애노테이션 사용 가능)  
  * postman으로 raw - JSON으로 데이터 전송  
  * 단순 텍스트와 같이 사용 가능
  * ```
    private ObjectMapper objectMapper = new ObjectMapper(); (Jackson 라이브러리) 
    objectMapper.readValue(문자, 클래스 타입); : 객체로 변환하는 것도 가능 
    ``` 
    
</br>    
    
## **HttpServletResponse**  
* Content  
  * ```response.setStatus(HttpServletResponse.SC_OK);``` : 상태 세팅  
  * ```response.setHeader(name, value);``` : 헤더 세팅 
  * ```request.setContentType("text/plain); ``` : 표현 데이터 세팅
  * ```request.getCharacterEncoding("utf-8);```  : 인코딩 정보 세팅  
  * ```request.setContentLength();``` : 생략시 

</br>

* Cookie  
  * ```response.setHeader(Set-Cookie, (key,value), Max-Age:600);``` : 쿠키 세팅  
  * 쿠키 객체 생성 후 ```response.addCookie(인스턴스);```하면 객체에 있는 파라미터 자동 주입

</br>

* Redirect  
  * ```response.setStatus(HttpServletResponse.SC_FOUND); ``` : 302 상태 코드  
  * ```response.setHeader("Location", "주소");, response.setRedirect("주소");``` : 리다이렉트  

</br>

## **HTTP 응답 데이터**  
* 단순 텍스트, HTML  
  * 직접 HTML작성으로(자바코드) 응답 가능  
  * 반환 시 ```text/html```로 지정 해야한다  

</br>

* API JSON  
  * 객체 값 초기화  
  * content-type을 ```application/json```로 지정
  * ```private ObjectMapper objectMapper = new ObjectMapper();``` 생성  
  * ```String result = objectMapper.writeValueAsString();```로 JSON(result)으로 변환  
  
</br>

## **정리**  
* 서블릿 지원하는 WAS 사용 시 직접 요청 HTTP 메시지, HTTP 응답 메시지 작성 필요 없음  
* start-line, 헤더 정보들을 조회,세팅 할 수 있음  
* 주로 GET - 쿼리 파라미터, POST - HTML Form, HTTP message body 3가지로 클라이언트에서 서버로 데이터 전달
  
 </br>
  
출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
