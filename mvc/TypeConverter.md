## **TypeConverter** ##
* 타입 컨버터 - Converter  
  * org.springframework.core.convert.converter.Converter 인터페이스 구현
  *      public interface Converter<S, T> {
               T convert(S source);
             }   
  *      @Slf4j
         public class StringToIntegerConverter implements Converter<String, Integer> {
             @Override
             public Integer convert(String source) {
             log.info("convert source={}", source);
             return Integer.valueOf(source);
             }
          }  
          
* 스프링에 Converter 적용하기  
  *       @Configuration
          public class WebConfig implements WebMvcConfigurer {
              @Override
              public void addFormatters(FormatterRegistry registry) {
              registry.addConverter(new StringToIntegerConverter());            
              }
           }
  * 스프링 내부에서 ConversionService를 제공하기 때문에 WebConfigurer가 제공하는 addFormatters()로 등록  
  * 추가한 컨버터 > 기본 컨버터 우선순위  
* 뷰 템플릿 적용  
  * 변수 표현식 : ${...}
  * 컨버전 서비스 적용 : ${{...}}  

</br>

## 포맷터 - Formatter  ##
  * 문자 <-> 다른 타입로 변환하는 상황이 대부분 ex) 1000 <-> "1,000" 
  * String print(T object, Locale locale) : 객체를 문자로 변경  
  * T parse(String text, Locale locale) : 문자를 객체로 변경  
  *         @Slf4j
            public class MyNumberFormatter implements Formatter<Number> {
                @Override
                public Number parse(String text, Locale locale) throws ParseException {
                log.info("text={}, locale={}", text, locale);
                NumberFormat format = NumberFormat.getInstance(locale);
                return format.parse(text);
                }
                @Override
                public String print(Number object, Locale locale) {
                log.info("object={}, locale={}", object, locale);
                return NumberFormat.getInstance(locale).format(object);
                }
            }  
  * 적용 : ```  registry.addFormatter(new MyNumberFormatter()); ```  
 * 스프링이 제공하는 기본 포맷터  
   * @NumberFormat : 숫자 관련 형식 지정 포맷터  
   * @DateTimeFormat : 날짜 관련 형식 지정 포맷터  

</br>

## 정리 ##
* 컨버전 서비스 적용은 기존에서 {}하나씩 추가한 ${{...}}
* 보통 포맷터 사용 ex) 1000원 <-> 1,000원 
* @NumberFormat은 숫자 관련 형식 지정 포맷터  
* @DateTimeFormat은 날짜 관련 형식 지정 포맷터
  
  </br>
  
출처 : 인프런 - 스프링 MVC 2편 - 백엔드 웹 개발 활용 기술
