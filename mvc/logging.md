## **로깅**
* 실무에선 System.out.println();을 사용하지 않음, 별도의 로깅 라이브러리를 사용해 로그 출력  
  * ```private Logger log = LoggerFactory.getLogger(getClass());```  
  * ```private static final Logger log = LoggerFactory.getLogger(Xxx.class);```  
  * ``@Slf4j`` 사용시 위 생략 가능
* 로그 레벨 설정 가능  

  ```log.trace("trace log={}", name);  
     log.debug("debug log={}", name);  
     log.info(" info log={}", name);  
     log.warn(" warn log={}, name);  
     log.error("error log={}", name);
  ```   
  * 패키지와 그 하위 로그 레벨 설정
  * ```logging.level.hello.springmvc=debug``` 일 경우 debug레벨부터 확인 
  * ```logging.level.root=info```로 기본설정되어 있음
  * 개발 서버는 debug 출력  
  * 운영 서버는 info 출력  
* 주의점  
  * ```log.trace("trace my log=" + name);```로 작성할 경우 연산이 일어남 ```String name = "Spring";``` 일 경우
  ```log.trace("trace my log=Spring");```이 된다  
* 장점  
  * 쓰레드 정보, 클래스 이름 같은 부가 정보 확인 가능, 출력 모양 조정 가능  
  * 로그 레벨에 따라 상황에 맞게 조절할 수 있음  
  * 파일, 네트워크 등 로그를 별도 위치에 남길 수 있음 특히 파일로 남길 때 일별, 특정 용량에 따라 분할 가능 
  * 성능이 System.out보다 좋음 실무에선 꼭 로그 사용  

</br>  

## **정리**
* 로그를 남길 때```@Slf4j```를 이용하자  
* 로그 레벨을 설정할 수 있음  
* 개발 서버 debug, 운영 서버 info  
* ```log.trace("trace my log=" + name);```가 아닌 ```log.trace("trace log={}", name);```형태로 사용하자  

</br>

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
  
