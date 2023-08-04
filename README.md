#### 1. Tomcat 서버를 시작할 때 웹 애플리케이션이 초기화하는 과정을 설명하라.
* 서블릿 컨테이너가 상태관리하는 ServletContext 생성
* ServletContext 초기화 이벤트
* ServletContextListener 골백 메소 contextInitialized
* jwp.sql 파일로 sql실행
* 서블릿 컨테이너는 클라이언트로부터 최초 요청시 DispatcherServlet 인스턴스 생성(-> loadOnStartup 속성 변경시 서블릿 컨테이너 시작시 인스턴스 생성)
* DispatcherServlet init() 으로 RequestMapping 객체를 통해 URL과 Controller 인스턴스 매핑
#### 2. Tomcat 서버를 시작한 후 http://localhost:8080으로 접근시 호출 순서 및 흐름을 설명하라.
* ResourceFilter, CharacterEncodingFilter의 doFilter()메소드 실행
* 정적자원이 아닌 "/"요청은 DispatcherServlet 의 service() 실행
* 해당 controller객체를 RequestMapping에서 가져와서 반환
* service()는 해당 Controller의 excute()메소드에 위임
* 반환받은 ModelAndView의 모델 데이터를 View의 render()로 전달, 응답

#### 7. next.web.qna package의 ShowController는 멀티 쓰레드 상황에서 문제가 발생하는 이유에 대해 설명하라.
* 스택 - 메소드인자, 로컬변수 등 각 쓰레드마다 서로 다른영역을 가짐.
* 힙   - 인스턴스의 상태 데이터 관리. 쓰레드가 서로 공유 가능.

* **로컬변수로 생성하면 공유하지 않기때문에 해결 가능**

./tt
