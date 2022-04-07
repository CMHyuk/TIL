## **스프링 MVC구조**  
![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162191398-62a195df-c7eb-4856-8986-92d0d680717a.png)   
* 동작순서
1. 핸들러 조회: 핸들러 매핑을 통해 요청 URL에 매핑된 핸들러(컨트롤러)를 조회한다.
2. 핸들러 어댑터 조회 : 핸들러를 실행할 수 있는 핸들러 어댑터를 조회한다.
3. 핸들러 어댑터 실행 : 핸들러 어댑터를 실행한다.
4. 핸들러 실행: 핸들러 어댑터가 실제 핸들러를 실행한다.
5. ModelAndView 반환 : 핸들러 어댑터는 핸들러가 반환하는 정보를 ModelAndView로 변환해서
반환한다.
6. viewResolver 호출 : 뷰 리졸버를 찾고 실행한다.
JSP의 경우: InternalResourceViewResolver 가 자동 등록되고, 사용된다.
7. View 반환 : 뷰 리졸버는 뷰의 논리 이름을 물리 이름으로 바꾸고, 렌더링 역할을 담당하는 뷰 객체를
반환한다.
JSP의 경우 InternalResourceView(JstlView) 를 반환하는데, 내부에 forward() 로직이 있다.
8. 뷰 렌더링 : 뷰를 통해서 뷰를 렌더링 한다.

</br>

## **@Controller, @RequestMapping** 
* @Controller : 스프링이 자동으로 스프링 빈 등록(내부에 @Component), RquestMappingHandlerMapping에서 핸들러 정보로 인식  
* @RequestMapping : 요청 정보를 매핑, 해당 URL이 호출되면 메서드 호출  
* RquestMappingHandlerMapping은 스프링 빈 중에서 @RequestMapping, @Controller가 클래스 레벨에 붙어 있는 경우 매핑 정보로 인식  

![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162191641-6975ab96-6c90-414d-ae1e-ba2947e1dbcd.png)

* RequestMappingHandlerAdapter가 매핑해서 준 애를 처리함

</br>

## **정리**  
* @Controller, @RequestMapping이 실무에서 가장 많이 사용 된다  
* 역할이 나눠져 유지 보수 용이

</br>  

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
