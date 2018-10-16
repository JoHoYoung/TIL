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
#### 9. Controller 클래스를 만드는데, 클래스가 만들어지는 위치가 중요하다. 위에서 언급했듯이 스프링부트는 메인클래스의 설정에 의해 컴포넌트스캔을 한다고 했었는데,스프링부트는 컴포넌트 스캔을 할 때, 기본적으로 메인클래스가 있는 위치를 기준으로 스캔을 하게된다.만약, AutoScan이 되어야 하는 컴포넌트 클래스들 - 대표적으로 @Controller, @Service, @Repository, @Component등의 위치가 메인클래스가 위치한 패키지보다  상위 패키지에 있거나, 하위가 아닌 다른 패키지에 있는 경우, 스캔이 되지 않는다.

### SpringBoot의 MVC 기본.
#### 1. view의 기본 - jsp를 사용하기 위한 중요한 설정. (이것 때문에 한참 삽질했다)
>pom.xml에
```
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
        </dependency>
        <dependency>
            <groupId>org.apache.tomcat.embed</groupId>
            <artifactId>tomcat-embed-jasper</artifactId>
            <scope>provided</scope>
        </dependency>
```
        를 추가헤 줘야함.
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
#### 2. application.properties설정
```
spring.datasource.url=jdbc:mysql://localhost:3306/dbs?useSSL=false
spring.datasource.username= 계정이름
spring.datasource.password= 비밀번호
```
> 드라이버는 spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver를 쓰지않으면 에러가 남(버전업데이트 관련인듯)
#### 3. Mybatis 설정파일 로드.
>mybatis.config-location=mybatis-config.xml
#### 4. 설정파일 생성. <mapper resource="MemberMapper.xml"/>
#### 5. Mapper.xml 파일에 함수등록, 함수에따른 쿼리 작성
```
<select id="selectMemberList" parameterType="com.example.demo.BoardDomain" resultType="com.example.demo.BoardDomain">
select * from board
</select>
```
#### 6. Mapper.java파일에 interface로 사용할 함수 등록
```
public interface BoardMapper {
    public List<BoardDomain> selectMemberList();
}
```
>함수에 따른 내부 코드는 xml파일로 작성 함.
#### 7. 다음에는 다중값 속성, insert, delete 도 해볼예정. multpart업로드도 구현해봐야 겠다.

### 웹에서부터의 Multipart에 대해.
#### 1. Front단은 똑같음.
```
<form type="multipart....">
input multiple="multiple" type="file" name="...."...>
</form>
```
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
            파일 이름을 받와와서 적절한 이름으로 변경
            String fileUrl = "/Users/HY/IdeaProjects/demo/src/main/webapp/WEB-INF/uploadFiles/";
            destinationFileName = RandomStringUtils.randomAlphanumeric(32) + "." + sourceFileNameExtension;
            destinationFile = new File(fileUrl + destinationFileName);]
            저장할 폴더 경로 + 적절하게 변경한 이름으로 파일 생성.
```
#### 9.multipart파일을 이파일에 덮어쓰기.
```
destinationFile.getParentFile().mkdirs();
               files.get(i).transferTo(destinationFile);
```
#### 10. post방식으로 넘어온 변수 처리에 대해.
>parameter에 HttpServletRequest request를 선언하고, equest.getParameter("id")같은 식으로 받아오면 된다.
엄청 노가다 뛰는걸로 알고 있었는데, 새로운걸 배웠다.

#### 11. 다중파일 업로드, 데이터베이스 연결까지 구현 했으니, 이제 CRUD를 만들어 봐야겠다. 그후, facebook OAUTH, 이메일 인증기능 까지 구현해보자.

### ORM(Object Relation Mapping)에 대해
#### 객체와 데이터베이스 불일치 문제를 해결하기 위한 도구.
#### MyBatis, JPA. MyBatis를 많이 썼지만 JPA를 많이 쓰는 추세라고 한다.
#### 기존에는 MyBatis를 사용할때는 mapper클래스, 그를 위한 xml, mybatis설정을 위한 xml파일 등 절차가 조금 복잡했으나, JPA를 쓰니 절차가 조금 더 간단해 졌다.
#### relation과 Mapping을 위한 class(model), 그를 구현하는 Repositry interface 만 구현하면, JPA에서 기본으로 제공하는 함수를 쓸 수 있어 편하다.
#### 또한 mybatis에서 query mapping을 하던 기능도 충분히 지원을 하니 JPA가 좋다고 생각 된다.

### JPA 사용을 위한 절차.
#### @Entity는 클래스가 데이터베이스 테이블을 매핑하는 역할을 한다.
#### @Repository는 Entity조작에 필요한 쿼리를 메서드화 해서 사용할 수 있는 역할을 한다.
#### 연관관계
> 1:1, 1:N, N:1, N:N @ManyToOne, @OneToMany
> @ManyToOne은 즉시 로딩이 기본값이다. 즉시 로딩으로 실행될 때는 연결된 엔티티 정보까지 한번에 가져오려고 하므로 성능에 문제가 생길 수 있다. 지연로딩 되도록 설정하는것이 좋다
. @ManyToOne(fetch = FetchType.LAZY)
> @OneToMany를 사용할 경우 mappedBy를 통해 주인을 명시해준다. @OneToMany(mapperBy = "school")
#### Repository.save(new entity)형식은 insert구문과 같다. 나머지는 update와 같다.
#### @AutoWired -> 의존성 주입. Repository사용할때 사용한다.


#### 1. Relation과 Mapping을 위한 Model 클래스 정의
> @Entity Anotation을 붙여줘야 함.
```
@Entity
public class board implements Serializable {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private int bno;
    private String username;
    private String contents;

    public board()
    {

    }

    public int  getBno()
    {
        return bno;
    }

    public String getUsername()
    {
        return username;
    }

    public String getContents()
    {
        return contents;
    }
}
```
#### 2. 사용을 위한 Repository 클래스 정의.
> @Repository Annotation을 붙여줘야 함.
```
@Repository
public interface BoardRepository extends JpaRepository<board, Long> {

    board findByusername(@Param("username")String username);
}
```
#### 3. 사용할 Controller에서 Autowierd설정 후 사용(의존성 주입)
```
@Autowired
  BoardRepository BoardRepository;
```
#### 4. JPA에서 제공하는 기본적인 CRUD함수.
```
반환타입 findBy필드명(Parameter);
board findByusername(@Param("username")String username);
```

#### 5. @Query Annotation을 사용해 함수를 만들 수 있다. 다만 JPQL로 작성하여야 하며, 별칭은 필수로 사용하여야한다. (이 부분때문에 오래걸림)
```
 SELECT m FROM Member AS m where m.username = 'HY'
 별칭을 지정하는 AS는 생략 가능하다.
 @Query("select u from board u where u.username = :myname")
    List<board> customfunc(@Param("myname") String name);
 ```
 > @Param 이 작동되지 않아 한참을 고생 하였다. 알고보니 mybatis에서 jpa로 바꾸는 중에 @Param을 mybatis패키지에서 받아와서 계속 에러가 나는 것이었다... 패키지를 바꿔주니 바로 해결 되었다.. 정말 허무하다.

 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
<img width="809" alt="2018-09-30 7 27 11" src="https://user-images.githubusercontent.com/37579650/46257612-bbb57e00-c4f7-11e8-99dd-ea79d445a24a.png">
<img width="807" alt="2018-09-30 7 27 17" src="https://user-images.githubusercontent.com/37579650/46257613-bbb57e00-c4f7-11e8-94c5-a9c4fed5445a.png">

### 6. @Modifying, @Query를 이용해 칼럼 속성을 바꾸는 함수를 작성하니
```
@Modifying
    @Query("update user_schema s set s.auth=1 where s.id=?1")
    void Authuser(@Param("id")String id);

javax.persistence.TransactionRequiredException: Executing an update/delete query
```

### 에러가 발생하였다. 원인을 찾지 못하겠다.
> @Modifying 뿐만아니라 @Transactional 어노테이션도 추가로 작성하니 작동하였다.
이것때문에 정말 고생한것 같다. @Transactional 어노테이션이 무슨역할을 하는지 알아봐야 겠다.
>@Transactional은 이름에서 알 수 있듯이 Transaction과 관련있는 것이라고 한다. DB시간에 배운 트랜잭션과 똑같은 것이다. 한 연산의 단위, 쿼리들의 집합... Modifying을 할

##JPA
JPA를 사용하지 않을때 문제.
jdbc를 직접사용.
Query가 대부분 비슷하지만 다른것도 많다.
반복적인 코드가 많다.
여러가지 문제를 해결하기 위해 ORM사용
spring boot에서는 Hikari 사용

도메인 모델 기반 사용.
객체지향의 장점을 활용하기 좋다.
각종 디자인패턴
코드 재사용
비즈니스 로직 구현 및 테스트 편함
ORM이란 애플리케이션의 클래스와 sql데이터베이스의 테이블 사이의 맵핑 정보를 기술한 메타데이터를 사용하여 객체를 sql데이터베이스의 테이블에 자동으로 영속화 해주는 기술

hibernate가 db에따라 알맞는 sql로 바꿔준

테이블과 테이블간의 외래키는 한 다른테이블의 주키를 외래키를 설정. 다른 두 테이블의 외래키설정 불가.

@Entity 이 클래스가 데이터베이스가 ~라는 테이블에 맵핑이되는 클래스다.
@id : 주키에 맵핑
@GenteratedValue: 자동으로 생성되는 값을 사용하겠다. db에 이미 테이블이 만들어져 있고, 그 값을 사용할때는 IDENTITY

spring.jpa.hibernate.ddl-auto=update, 업데이트 , create 로 하면 매번 지우고 새롭게 만드는것이다.
> Entity class에 속성 추가하면 relation에 자동으로 추가된다.

@Entity 맵핑
Annotation 기반 설정
@Entity는 자동으로 테이블로 맵핑 사실상 @Table Annotation이 생략되어 있음. 기본적으로 클래스 이름과 동일한 엔티티 사용
@Entity(name="sdasad")으로 엔티티 맵핑 변경
@Table에서 사용하는 기본 값이 Entity의 이름이다. 아무런 설정을 하지 않으면 기본적으로 클래스이름과 같은 entity맵핑.


db에서 User키워드가 있어서 사용할 수 없다. @Entitiy(name = "fdsafsd") 의 맵핑은 맵핑되는 릴레이션의 정보를 바꾸는 것이 아니라, 사용될 Entity 클래스의 이름을 설정해 주는것. 엔티티 이름을 이와같은 방법을 통해 바꿀 수 있다.

@Column(nullable = false, unique = true);

@Temporal 어노테이션
```
@Temproal(TemporalType.TIMESTAMP)으로 설정하면 날짜 시간,
@Temproal(TemporalType.TIME) - > 시간만.

@Transient 를 추가하면 column으로 만들지 않는다
```

@Transient
private String no; 라고 하면 테이블에 no 속성이 추가되지 않는다

Class ->  Entity Type
vairable -> Value Type

기본적으로 db에서 쿼리를 만드는것이 아니라 JAP로 Entity클래스를 선언하면 DB에 테이블이 형성된다.

Value타입 매핑.
@Embadable 어노테이션 사용하여 클래스 하나 정의, 그 클래스를 value로 갖는 클래스에서

private Adress temp 라고 선언하면 Address 클래스의 요소가 db테이블의 속성으로 추가된다.

```
@Embeded
@AttributePverrodes({
  @AttributePverride(name="street", column=@Column(name="home_street") )
  })
```
  private Address adress로 오버라이딩 해서 사용 가능. Address의 street 요소가 home_street라는 이름으로 들어오게 된다.

  1대다 맵핑 @OneToMany
  어떤 엔티티가 있고 다른 엔티티가 있다.
  관계는 항상 두가지 엔티티가 맞물려 있다.

  속성이 collection이 아닌쪽이 one

  Owner 테이블에서 외래키를 생성하고 갖고있게 된다. 그 외래키는 상대 엔티티의 id를 참조한다.

  어떤관계의 주인 이라는건 관계를 설정했을때 그 값이 반영이 되는것.

@ManyToOne은 외래키만 추가하는 반면
@OneToMany는 조인테이블을 새로 만든다. 그 테이블에 관계에 대한 정보가 저장되며 외래키를 따로 생성하지 않는다.

서로 참조하는 양방향 관계를 만들 수도 있다. 양쪽에 OneToMany, ManyToOne을 선언하면 양방향 맵핑이라고 생각할 수 있지만 이것은 두개의 단방향 관계이다. 양방향 관계를 설정하려면 따로 설정을 해줘야한다. 양방향 관계를 설정하려면
@OneToMany(mappedBy = "owner")를 정의 해야하며 mappedBy 는 OneToMany쪽에 정의.
이때 관계를 설정시에 양쪽에 둘다 관계를 설정해 주어야 한다. @OneToMany인 쪽에 .add.. 를 해주고 @ManyToOne에 setOwner설정을 양쪽으로 설정해주어야 정상적으로 관계 형성이됨. 양방향 관계인데 한쪽에만 add혹은 set 해준다는건 맞지않는것. add는 필수적으로 수행해야하는 코드는 아니다. 하지만 객체지향적으로 생각했을때 둘다 하는것이 좋다.

이상적인 것은 Convenient method를 만들어 사용하는 것.
```
public addStudy(Study study)
{
  this.getStudies().add(study);
  study.setOwner(this);
}

public removeStudy(Study study)
{
  this.getStudies().add(study);
  study.setOwner(null);
}
```

Entity의 상태 Cascade Option.
@OneToMany, @ManyToOne에 Cascade 옵션이 있다.
cascade란 entity의 상태변화를 전이시키는 것.
상태는 크게 4가지가 있다. Transient Removed Persistant Detached
Transient : 객체가 db에 저장될지 안될지 jpa, hibernate가 전혀 모르는 상태. save하기 전.
SAVE를 하면 persistent상태가 된다. save를 한다고 객체가 바로 들어가는 것은 아니다. 이 상태로 관리하고 있다가 이쯤 됐으면 db에 넣어야 겠다. 판단하는 그 시점에 저장하게 된다. save를 호출했다고 해서 그 즉시 insert 쿼리가 발생하는 것은 아니다. save를 호출하면 hibernate가 아는 상태 persistant 1차캐쉬. 인스턴스가 cache가 된 상태. 이상태에서 다시한번 이 인스턴스를 달라고 하면 셀렉트 쿼리가 발생하지 않는다. cache하고 있는걸 줄게 하며 준다. db에서 나오는것이 아님. 저장을 하지도 않은 상태에서 주는것. transaction이 끝나는 즉 commit이 일어나면, insert쿼리가 발생한다. -> 중간에 값을 바꾸는등 불필요한 액션을 취하지 않는 장점. 객체를 계속 감시하고 있다가 트랜잭션이 끝나면 쿼리 수행. ( Dirty checking 이 객체의 변경사항을 계속 감지한다.)

removed상태에 머물러 있다가 commit이 일어날때 삭제한다.

 hibernate가 persistant 상태로 관리하고 있다.
@OneToMany(cascade =  )

예를들어 게시글과 댓글의 관계. 게시글이 삭제되면 댓글도 삭제되어야 한다.
```
@Entitiy
public class Post{

@id @GeneratedValue
private long id

private Set<comment> comments = new HashSet<>();

public void addComment(Comment comment){
  this.getComments.add(comment);
  comment.setPost(this)
}

@Entity
public class Comment{

@id @GeneratedValue
private long id;

@OneToMany(mappedby = "post")
private Post post;


}

@OneToMany(cascade =CascadeType.PERSIST)로 설정을 하면. post.save()로 저장을 할때 이 persistant를 알려주세요. transient에서 넘어갈때 같이 persistant가되고 저장이 된다. CascadeType.REMOVE 설정은 지울때 포스트를 삭제하는순간 removed상태가 전파가 되고 comment도 removed상태가 돼서 같이 지워준다. 그냥 CASCADETYE.ALL로 전부 전파하도록 설정하면 편하다.
```

Fetch 연관관계의 엔티티를 어떻게 가져올것인가. 지(Eager?) 나중에(Lazy?) .

OneToMany는 기본적으로 Lazy 많으니까.
ManyToOne은 기본적으로 Eager. 생각해보면 합리적이다.

이 default설정 lazy로 인해, 예를들어 post에 적혀있는 comment로 가져올때 n+1셀렉트 에러가 생길수 있다. 이런 fetch전략을 잘 정하는게 성능에 큰 영향을 미침.

스프링 데이터 JPA.
data access object 역할을 하는 repository를 정의.

```
@Repository
@Transactional
public class PostRepository{

  @AutoWired 보다
  @PersisenceContext를 쓰는게 좋다.
  스프링 코드를 최대한 감추는게 JPA의 원칙이라..
  EntityManager entitiyManager;

  public Post add(Post post)
  {
    entitiyManager.persist(post);
    return post;
  }

  public void delete(Post post){
    EntityManager.remover(post);
  }

}
이렇게 잘 쓰지 않는다.
```

훨씬 편리한 방법. 최근에 가장 진보된 형태

```
@Repository
public interface PostRepository extends JpaRepository<Post, Long>{


}
```

원래는 @EnableJpaRepositories를 붙여야 하는데 @SpringBootApplication이 자동으로 설정 해 준다.

쿼리를 띄웠을때 ?로 나타나는 값을 보는 방법. 쿼리 확인안하고 할거면 hibernate를 쓰지마라. 성능에 문제가 생길 수 있다.
```
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=TransactionRequiredException
loggin.level.org.hibernate.type.descriptor.sql=trace
```

SpringData Common
상속받아서 Interface를 만든 JpaRepository는 Repository(기능 x), CrudRepository, PagingAndSortingRepository //스프링데이터 Common// 에서 기능을 더 추가한것.

이러한 것들은 @NoRepositoryBean Annotation이 붙어있어 빈을 만들어서 등록하는것을 방지한다. (이것을 상속받아 사용하라는 것. 중간단계 Repository, 실제 Repository가 아님을 의미)

CrudRepository : Save, SaveAll, findById, existsById(존재유무 판단), findAll, findAllById

@Test의 경우는 어차피 모두 rollback이기 때문에 hibernate가 실제로 쿼리를 날리지 않는다.

PagingAndSortingRepository : findAll(Pageable page)
postRepository.findAll(PageRequest.of(0,10)) new PageRequest 에서 PageRequest.of로 바뀜. deprecated가 발생한다.

null처리
Optional은 null이 없다. isEmpty사용.
