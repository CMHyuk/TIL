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

## **정리**  
* 서블릿 지원하는 WAS 사용 시 직접 요청 HTTP 메시지, HTTP 응답 메시지 작성 필요 없음  
  
 </br>
  
출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
