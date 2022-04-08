## **요청파라미터**  
* @RequestParam : 파라미터 이름으로 바인딩(입력)  
  * HTTP 파라미터 이름이 변수 이름과 같으면 생략 가능  
  * 단순 타입(String, int, Integer)이면 @RequestParam도 생략 가능, 생략시 required = false로 설정  
    ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162443405-37651a8a-f13a-4533-bc7c-53c9d5e9fd48.png)
  * required = fasle면 파라미터 값 생략 가능(기본값은 required = true)  
  * defaultValue : 기본 값 적용(빈 문자 경우에도 적용), required는 불필요 작성시 무시  
    ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162443628-19d9acfe-1e4c-4ec7-a854-489938da5bf6.png)     
* @ResponseBody : View무시 직접 입력  
* @RequestParam Map, MultiValueMap 파라미터 값 1개면 Map 아니면 MultiValueMap 보통 Map사용  
* @ModelAttribute : 객체 생성, 파라미터 값(자동)  
   ![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162445445-81b2c08c-7cac-4a95-94e6-3090e67d0e6e.png)
  * 객체를 생성 후 객체의 프로퍼티를 찾아 setter를 호출해 파라미터 값을 바인딩 함  
  * 프로퍼티 ex) getUsername(), setUsername() 메서드가 있으면 username이라는 프로퍼티를 가지고 있음  
  * 파라미터 값 타입이 안 맞으면 BindException이 발생  
* @Data  
  * @Getter, @Setter, @ToString, @EqualsAndHashCode, @RequiredArgsConstructor를 자동 적용 
