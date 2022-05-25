## **@ModelAttribute** ##
* 객체를 생성하고 요청 파라미터 값을 프로퍼티 접근법(set.xx)로 처리해줌  
* Model에 자동으로 @ModelAttribute로 지정한 객체를 넣어줌  
* @ModelAttribute("item") Item item이면 item이름으로 저장  
* @ModelAttribute() Item item이면 Item -> item처럼 첫글자만 소문자로 바꿔 저장
* @ModelAttribute 생략 가능 (기본 타입은 @RequestParam으로 작동)  

</br>

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
