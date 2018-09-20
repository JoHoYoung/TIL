# TIL-Spring_boot
Today i learned about spring-boot

### 서블릿 이란
> 웹프로그래밍에서 클라이언트의 요청을 처리하고 그 결과를 다시 클라이언트에게 전송하는 Servlet 클래스의 구현 규칙을 지킨 자바 프로그래밍 기술
MVC 패턴에서 Controller 같은 것. start -> initialize -> service -> destroy

### spring-boot로 초기셋팅.
#### 1. spring boot 플러그인 설치
#### 2. 플러그인을 설치하면 spring intiaizr가 생김.
#### 3. 이걸 선택해서 프로젝트 생성.
#### 4. Web 라이브러리 선택.
#### 5. SpringBoot는 어플리케이션이 시작될때 필요한 기본 설정들을 자동으로 설정하게 되어 있는데 (Auto Configuration) 그 중 DataSource설정이 자동구성 될 때 필요한 Database Type 정보들이 설정되어 있지 않아서 에러가 난다.
#### 6. db를 결정하지 않은 경우 메인 클래스에 @EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class}) 추가.
#### 7. SpringBoot는 프로젝트가 생성될때 Web라이브러리가 포함된 경우, 정적인 웹리소스는 src > main > resources > static 아래에서 관리되도록 설정된다. 즉, html, css, js, image등의 정적컨텐츠는 static아래에 위치시키면 접근가능하고, static이 루트폴더가 된다는 의미이다.프로젝트를 생성할 당시, 라이브러를 추가할때 Web 라이브러를 추가했다면 static 폴더가 자동으로 만들어진다.
#### 7. Index.html이 기본인듯 하다. 기본설정은 어떻게 바꾸는 걸까?
#### 8. 포트는 기본이 8080인듯 한데 포트는 어떻게 바꾸는 것일까?
> 포트는 application.properties에서 server.port=num 으로 기본 port를 바꿀 수 있다고 한다.
#### 9. Controller 클래스를 만드는데, 클래스가 만들어지는 위치가 중요하다. 위에서 언급했듯이 스프링부트는 메인클래스의 설정에 의해 컴포넌트스캔을 한다고 했었는데,스프링부트는 컴포넌트 스캔을 할 때, 기본적으로 메인클래스가 있는 위치를 기준으로 스캔을 하게된다.만약, AutoScan이 되어야 하는 컴포넌트 클래스들 - 대표적으로 @Controller, @Service, @Repository, @Component등-의 위치가 메인클래스가 위치한 패키지보다  상위 패키지에 있거나, 하위가 아닌 다른 패키지에 있는 경우, 스캔이 되지 않는다. 출처: http://yonguri.tistory.com/entry/스프링부트-SpringBoot-개발환경-구성-2-MVC-환경구성 [Yorath's 블로그]

### SpringBoot의 MVC 기본.
#### 1. view의 기본 - jsp를 사용하기 위한 중요한 설정. (이것 때문에 한참 삽질했다)
>pom.xml에 <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
        </dependency>
        <dependency>
            <groupId>org.apache.tomcat.embed</groupId>
            <artifactId>tomcat-embed-jasper</artifactId>
            <scope>provided</scope>
        </dependency> 를 추가헤 줘야함.
        그리고 기본 설정으로 spring.mvc.view.prefix=/WEB-INF/views/
          spring.mvc.view.suffix=.jsp 경로에 있는 .jsp파일을 실행하겠단 의미.
#### 2. controller의 기.
> 같은 패키지에 controller 폴더를 만들고 class 파일 추가. @Controller 를 해줘야 boot가 자동으로 component scan할 때 scan 함. 메인 class @ComponentScan(basePackages = "com.example.demo") 예를 들어 return "hello"를 하면 기본설정에서 지정한 prefix, suffix가 붙어 /WEB-INF/views/hello.jsp 가 실헹되는 구조이다.
#### 3. Project Structure -> Facets 에서 경로설정도 해줘야함. 

#### 4. MVC 패턴이라 그런지 Ruby On rails, Node express와 비슷한거 같아, 스트레스를 받진 않는다.
