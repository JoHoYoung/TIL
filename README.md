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
#### 2. controller의 기본.
> 같은 패키지에 controller 폴더를 만들고 class 파일 추가. @Controller 를 해줘야 boot가 자동으로 component scan할 때 scan 함. 메인 class @ComponentScan(basePackages = "com.example.demo") 예를 들어 return "hello"를 하면 기본설정에서 지정한 prefix, suffix가 붙어 /WEB-INF/views/hello.jsp 가 실헹되는 구조이다.
@RestController는 그 자체가 몸체가 되므로 뷰페이지 없이, return 으로 바로 html을 띄우는 방식이다.
#### 3. Project Structure -> Facets 에서 경로설정도 해줘야함.

#### 4. MVC 패턴이라 그런지 Ruby On rails, Node express와 비슷한거 같아, 스트레스를 받진 않는다.

### View 템플릿에 대해.
#### 1. 스프링 부트에서는 JSP를 권고하지 않아, Thymeleaf 사용.
#### 2. xml에 thymeleaf의존성을 맨 마지막에 추가 했더니 기존에 작성한 JSP관련 코드는 작동하지 않음. 아마도 Overwrite되는 듯 하다.
#### 3. thymeleaf를 쓰기 위해서는 html에 링크를 추가해줘야 함.

### HTTP Method.
#### 1.@RequestMapping(value="/post",method=RequestMethod.POST) 이런식으로 GET, POST 조절
> Express와 별 차이점 없어 보인다.
#### 2. Post방식으로 넘어오는 Parameter 처리.
> @RequestParam(value="id")Object id
#### 3. URI 템플릿. PathParameter에 대해.
> Express 에서는 '/post/:num' 에 대해 path.parse(req.params.num).base; 과 같은 식으로 받아왔었으나 Spring Boot에서는 value="/post/{num}"에 대해 @PathVariable int num 와 같은 방식으로 받아오며, 클라이언트에서 서버로 전송하는것은 별 차이 없음. 아직까지는 Node Express와 별 차이가 없어 할만한 듯 하다.


###Database MySQL 계정생성
#### 1. 데이터 베이스 생성 create database;
#### 2. 계정 생성 create user hy identified by '1234';
#### 3. 계정에 권한 부여 grant all privileges on dbs.* to hy;
#### 4. flush.

###Database MySQL - SpringBoot 연결 (With mybatis)
#### 1. maven 추가.
#### 2. application.properties설정 spring.datasource.url=jdbc:mysql://localhost:3306/dbs?useSSL=false
spring.datasource.username= 계정이름
spring.datasource.password= 비밀번호
> 드라이버는 spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver를 쓰지않으면 에러가 남(버전업데이트 관련인듯)
#### 3. Mybatis 설정파일 로드.
>mybatis.config-location=mybatis-config.xml
#### 4. 설정파일 생성. <mapper resource="MemberMapper.xml"/>
#### 5. Mapper.xml 파일에 함수등록, 함수에따른 쿼리 작성 <select id="selectMemberList" parameterType="com.example.demo.BoardDomain" resultType="com.example.demo.BoardDomain">
        select * from board
    </select>
#### 6. Mapper.java파일에 interface로 사용할 함수 등록 public interface BoardMapper {
    public List<BoardDomain> selectMemberList();
}
>함수에 따른 내부 코드는 xml파일로 작성 함.
#### 7. 다음에는 다중값 속성, insert, delete 도 해볼예정. multpart업로드도 구현해봐야 겠다.

### 웹에서부터의 Multipart에 대해.
#### 1. Front단은 똑같음. <form type="multipart....">
<input multiple="multiple" type="file" name="...."...>
</form>
#### 2. 프론트단 form태그에서 file태그의 이름으로 서버에 @RequestParam("userimage") List<MultipartFile> files parameter선언.
#### 3. 사진파일을 여러개 업로드 할 경우 때문에 List로 선언.
#### 4. for문을 이용하여 하나의 사진 올리는 과정을 갯수만큼 반복.
#### 5. 하나 올리는 과정.
#### 6. nodejs에서 multer로 구현해 보았으나, 만들어진 모듈을 사용하는거라 그런지 잘 이해되지 않았음.
#### 7. 스프링에서 구현해 본 결과, 일단 경로, 이름으로 빈 파일을 하나 만들고 입력받은 multipart파일을 만든 빈 파일에 덮어쓰는 식인듯 함.
#### 8.
```
String sourceFileName = files.get(i).getOriginalFilename();
            String sourceFileNameExtension = FilenameUtils.getExtension(sourceFileName).toLowerCase();
```
            파일 이름을 받와와서 적절한 이름으로 변경
            ~~~
            String fileUrl = "/Users/HY/IdeaProjects/demo/src/main/webapp/WEB-INF/uploadFiles/";
            destinationFileName = RandomStringUtils.randomAlphanumeric(32) + "." + sourceFileNameExtension;
            destinationFile = new File(fileUrl + destinationFileName);
            ~~~
            저장할 폴더 경로 + 적절하게 변경한 이름으로 파일 생성.
#### 9.multipart파일을 이파일에 덮어쓰기.
~~~
destinationFile.getParentFile().mkdirs();
               files.get(i).transferTo(destinationFile);
~~~
#### 10. post방식으로 넘어온 변수 처리에 대해.
>parameter에 HttpServletRequest request를 선언하고, equest.getParameter("id")같은 식으로 받아오면 된다.
엄청 노가다 뛰는걸로 알고 있었는데, 새로운걸 배웠다.

#### 11. 다중파일 업로드, 데이터베이스 연결까지 구현 했으니, 이제 CRUD를 만들어 봐야겠다. 그후, facebook OAUTH, 이메일 인증기능 까지 구현해보자.
