## **@ResponseBody 사용 원리**
![width="200px" height="100px"](https://user-images.githubusercontent.com/97818720/162620016-588dec74-4f1b-4891-90c1-5bbf587de973.png)
* @ResponseBody 사용  
  * HTTP BODY에 문자 내용 반환  
  * ```viewResolver``` 대신 ``HttpMessageConverter`` 동작  
  * 기분 문자 처리 ```StringHttpMessageConverter```
  * 기본 객체 처리 ```MappingJackson2HttpMessageConverter```  

## **HTTP 메시지 컨버터 적용**  
* 이를 사용시 HTTP 메시지 컨버터가 적용된다
  * HTTP 요청 : ```@RequestBody , HttpEntity(RequestEntity)```  
  * HTTP 응답 : ```@ResponseBody , HttpEntity(ResponseEntity)```  
``` package org.springframework.http.converter;

public interface HttpMessageConverter<T> {

boolean canRead(Class<?> clazz, @Nullable MediaType mediaType);
boolean canWrite(Class<?> clazz, @Nullable MediaType mediaType);

List<MediaType> getSupportedMediaTypes();

T read(Class<? extends T> clazz, HttpInputMessage inputMessage)
  throws IOException, HttpMessageNotReadableException;
void write(T t, @Nullable MediaType contentType, HttpOutputMessage 
outputMessage)
  throws IOException, HttpMessageNotWritableException;
  
}
```

* ```canRead(), canWrite()``` : 메시지 컨버터가 해당 클래스, 미디어 타입을 지원하는지 체크  
* ```read(), write()``` : 메시지 컨버터를 통해 메시지를 읽고 쓰는 기능  

</br>

## **스프링 부트 기본 메시지 컨버터**
``` 
0 = ByteArrayHttpMessageConverter  
1 = StringHttpMessageConverter  
2 = MappingJackson2HttpMessageConverter
```  
* 대상 클래스 타입과 미디어 타입 둘을 체크해 사용여부 결정  
* ``ByteArrayHttpMessageConverter`` : ``byte[]`` 데이터 처리  
  * 클래스 타입 : ``byte[]``, 미디어타입 : ``*/*``  
  * 요청 예 : ``@RequestBody byte[] data`` 
  * 응답 예 : ``@ResponseBody return byte[]`` 쓰기 미디어타입 ``application/octet-stream``  

* ``StringHttpMessageConverter`` : ``String`` 문자로 데이터를 처리  
  * 클래스 타입: String , 미디어타입: */*  
  * 요청 예 : ``@RequestBody String data``  
  * 응답 예 : ``@ResponseBody return "ok"`` 쓰기 미디어타입 ``text/plain``  

* ``MappingJackson2HttpMessageConverter`` : ``application/json``  
  * 클래스 타입: 객체 또는 HashMap , 미디어타입 application/json 관련 
  * 요청 예 : ``@RequestBody HelloData data``  
  * 응답 예 : ``@ResponseBody return helloData`` 쓰기 미디어타입 ``application/json 관련``  

```
content-type: text/html
@RequestMapping
void hello(@RequetsBody HelloData data) {}
```
위와 같은 요청 시 컨버터를 찾을 수 없거나, 컨버팅을 할 수 없다는 예외발생  

</br>

## **HTTP 요청 데이터 읽기, 생성**
* HTTP 요청 데이터 읽기  
  * HTTP 요청이 오고, 컨트롤러에서 ``@RequestBody , HttpEntity`` 파라미터를 사용 
  * 메시지 컨버터가 메시지를 읽을 수 있는지 확인하기 위해 ``canRead()`` 를 호출  
  * 대상 클래스 타입, HTTP 요청의 Content-Type 미디어 타입을 지원하는지 확인  
  * ``canRead()``조건 만족하면 ``read()``를 호출해 객채 생성 후 반환  

* HTTP 응답 데이터 생성  
  * 컨트롤러에서 ``@ResponseBody , HttpEntity`` 로 값이 반환  
  * 메시지 컨버터가 메시지를 쓸 수 있는지 확인하기 위해 ``canWrite()`` 를 호출  
  * 대상 클래스 타입, HTTP 요청의 Accept 미디어 타입을 지원하는지 확인  
  * ``canWrite()`` 조건을 만족하면 ``write()`` 를 호출해서 HTTP 응답 메시지 바디에 데이터를 생성  

* Accpet는 클라이언트가 서버에 요청할때 보내는 정보(클라 : "난 text/html을 해석할 수 있어")  
* content/type 은 서버가 클라이언트에 응답할때 보내는 정보(서버 : "이 리소스는 text/html이야 html로 해석해")  

</br>

## **정리**
* HTTP 요청은 ```@RequestBody , HttpEntity(RequestEntity)``` 
HTTP 응답은 ```@ResponseBody , HttpEntity(ResponseEntity)``` 의 경우 HTTP 메시지 컨버터가 적용됨  
* 요청의 경우 canRead()호출 -> 클래스 타입, Content-Type 타입 지원하는지 확인 -> 조건 만족시 read()를 호출해 객체 생성 후 반환  
* 응답의 경우 canWrite()호출 -> 클래스 타입, Accept 미디어 타입 지원하는지 확인 -> 
조건 만족시 write()를 호출해 HTTP 응답 메시지 바디에 데이터를 생성  

</br>

출처 : 인프런 - 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술
