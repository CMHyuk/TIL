## **JSP 라이브러리 추가**  
```
implementation 'org.apache.tomcat.embed:tomcat-embed-jasper'
implementation 'javax.servlet:jstl'
``` 
추가 후 Gradle refresh 해주기  

</br>  

## **서블릿과 JSP의 한계**  
* 서블릿으로 개발 시 HTML 작업이 자바 코드에 섞여 지저분, 복잡  
* JSP로 HTML 작업을 나눌 수 있지만 다양한 코드가 JSP에 노출되어 있음(너무 많은 역할)  

</br>  

## **MVC 패턴**  
* ```dispatcher.forward()``` : 다른 서블릿이나 JSP로 이동할 수 있는 기능, 서버 내부에서 다시 호출  
* redirect vs forward  
  * redirect : 웹 브라우저에 응답이 나갔다가, 클라이언트가 redirect 경로로 다시 요청 URL 경로 변경  
  * forward : 서버내부에서 일어나는 호출, 클라이언트가 인지 x  
* ```/WEB-INF``` : 이 경로안에 JSP가 있으면 외부에서 호출 불가능  
* 한계  
  * View로 이동하는 코드가 항상 중복  
  * ```HttpServletRequest request, HttpServletResponse response``` : request나 response 사용하지 않을 때도 있음  
  * 공통 처리가 어려움  
  * 프론트 컨트롤러 패턴도입으로 해결 가능  

</br>  

## **FrontController 패턴**  
* 프론트 컨트롤러 서블릿 하나로 클라이언트의 요청을 받음  
* 요청에 맞는 컨트롤러 찾아 호출(입구가 하나)  
* 공통 처리 가능  

* 프론트 컨트롤러 도입  
* View 분류  
  * 반복 되는 뷰 로직 분리
* Model 추가  
  * 서블릿 종속성 제거  
  * 뷰 이름 중복 제거
