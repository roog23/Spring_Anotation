# Spring_Anotation

Spring Framework annotations
=
Spring은 종속성을 주입을 사용하여 애플리케이션을 구성하고 바인딩을 함   

@Configuration
-
클래스를 Bean 정의의 소스로 표시하는데 사용   
Bean은 함께 연결하려는 시스템 구성요소, @Bean 표시된 메소드는 Bean 생산자   
Spring은 Bean의 라이프 사이클을 처리하며, Bean을 생성하기 위해 이러한 메소드를 사용   

@ComponentScan
-
Spring이 구성 클래스에 대해 알고 있고 Bean을 올바르게 초기화 할 수 있는지 확인하는데 사용   
Spring은 @Configuration 클래스에 대해 구성된 패키지를 스캔   

@Import
-
구성 클래스를 더 정밀한 제어 해야하는 경우 추가 구성을 로드하는데 사용   

@Component
-
Bean을 선언하는 또 다른 방법 @Component 주석으로 클래스를 표시   
자동 스캔 시간에 클래스가 Spring Bean으로 변경

@Service 
-
@Component의 전문화를 표시   
일반 구성 요소보다 더 자유롭게 관리하는 것이 안전하다고 Spring에 알림.   
서비스에는 캡슐화 된 상태가 없음

@Autowired
-
응용 프로그램 부분을 함께 연결하려면 구성 요소의 필드, 생성자 또는 메서드에서 @Autowired를 사용   
Spring의 의존성 주입 메커니즘은 @Autowired로 표시된 클래스 멤버에 적절한 빈을 연결

@Lazy
-
@Bean 또는 @Component를 @Lazy로 표시하여 요청시 초기화 되도록 사용   
요청시 빈 초기화

@Qualifier
-
@Autowired로 표시된 필드에 연결할 수 있는 여러 Bean이 있는 경우 @Qualifier를 사용하여 사용해야하는 Bean을 필터링   

@Value
-
속성을 초기화 할 필드 또는 매개 변수에 대한 기본값 표현식 표시    
일반적으로 구성 속성을 참조하는 것이 사용됨 ("#{systemProperties.myProp}")

@Required
-
시스템을 더 견고하게 만들기 위해 autowire할 Bean을 찾을 수 없을 때 Spring이 실패하도록 검증을 활성화   
종속성을 삽입 할 수 없는 경우 @Required를 사용하여 연결을 실패함   

Spring Boot and Web annotations
=
@SpringBootApplication
-
@Configuration, @EnableAutoConfiguration, @ConponentScan 주석이 결합되어 기본 속성으로 구성

@Configuration, @ConponentScan
-
Spring이 애플리케이션의 Bean 및 구성 요소를 만들고 구성하도록 함   
앱을 함께 연결하는 것에서 실제 비즈니스 로직 코드를 분리하는 좋은 방법

@EnableAutoConfiguration
-
Spring은 클래스 경로에서 사용 가능한 JAR 파일을 기반으로 구성을 추측   
사용하는 라이브러리를 파악하고 해당 구성 요소를 사전에 구성 가능   
모든 spring-boot-starter 라이브러리가 작동하는 방식    

@Controller
-
클래스를 HTTP 요청을 처리 할 수 있는 웹 컨트롤러를 표시   
Spring은 @Controller 주석으로 표시된 클래스의 메소드를 살펴보고 어떤 메소드가 어떤 엔드 포인트를 제공하는지 알기 위해 라우팅 테이블을 설정

@ResponseBody
-
Spring이 HTTP 응답 본문에서 바인딩 매서드의 반환 값을 만들어줌    

@RestController
-
@Controller 와 @ResponseBody를 함께 사용하는 편리한 구문
표시된 클래스의 모든 작업 메서드가 JSON 응답을 반환   

@RequestMappin(method = RequestMethod.GET, value="/path")
-
컨트롤러에서 지정된 경로에 대한 HTTP 요청을 처리할 방법을 지정   
Spring은 어떻게 수행되는지에 대한 구현 세부 사항을 처리    
주석에 경로 값을 지정하면 Spring이 요청을 올바른 작업 메서드로 라우팅함   

@RequestParam(value="name",defaultValue="World")
-
요청을 처리하는 메서드는 매개 변수를 사용할 수 있음   
HTTP 매개 변수를 작업 메서드 인수에 바인딩하는데 도움이 되도록 주석을 사용   
Spring은 요청 매개 변수를 구문 분석하고 적절한 매개 변수를 메소드 인수에 넣음   

@PathVariable("placeholderName")
-
정보르 제공하는 또 다른 일반적인 방법은 URL로 인코딩 하는 것
URL의 값을 매서드 인수로 가져올 수 있음

Spring Cloud annotations
=
웹 앱으로 구성된 더 큰 시스템을 구축하려는 경우 더 많은 작업을 해야함   
여러 앱을 구성하는 방법, 서로 통신하는 방법, 네트워크 오류로 인해 전체 시스템이 충돌하지 않는지 확인하는 방법과 같은 문제를 해결하기위해 사용   

@EnableConfigServer
-
애플리케이션을 다른 앱이 구성을 가져올 수 있는 서버로 전환   
모든 적절한 구성의 중앙 저장소를 보유하려면 구성 서버가 필요   
하나를 만드는 것이 주석 하나라는 장점   
중앙 구성 서버를 사용할 수 있을 때 클라이언트 Spring 앱 의 spring.application.cloud.config.uri 속성을 사용 하여 구성 서버를 가리킬 수 있음   
앱이 시작되면서 구성 서버에 연결하여 필요한 속성을 얻음, 구성을 앱코드와 함께 패키징 할 필요가 없음    
우려 사항 분리는 배포를 단순화하는데 효과적   

 @EnableEurekaServer 
 -
 주석을 추가하면 Eureka 검색 서비스가 됨, 다른 앱이 이를 통해 서비스를 찾을 수 있음   
 이를 사용하려면 앱에 Eureka 서버의 클라이언트가 되어야한다고 지시해야 함   
 
 @EnableDiscoveryClient
 -
 앱이 서비스 검색 서버에 등록되고 필요한 다른 서비스를 검색하기 위해 해당 서버에 문의함   
 모든 앱이 검색 클라이언트를 사용한느 경우 IP주소나 URL을 하드 코딩하지 않아도 됨
 
  @EnableCircuitBreaker
  -
  앱에서 회로 차단기 패턴을 인식하도록 하기 위한 주석   
  애플리케이션에 대한 Hystrix 회로 차단기 프로토콜이 구성   
  
   @HystrixCommand (fallbackMethod = "fallbackMethodName")
   -
   메서드가 예외를 발생 시키거나 시간이 초과되는 긴급 상황에서 앱이 Fallback 메서드를 사용해야함을 의미   
   모든 것이 작동 할 때 이 접근 방식은 코드를 깔끔하고 유지 관리 할 수 있도록 유지하는데 도움이 됨   
