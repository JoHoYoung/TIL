# TIL-Spring_boot
Today i learned about spring-boot

### ���� �̶�
> �����α׷��ֿ��� Ŭ���̾�Ʈ�� ��û�� ó���ϰ� �� ����� �ٽ� Ŭ���̾�Ʈ���� �����ϴ� Servlet Ŭ������ ���� ��Ģ�� ��Ų �ڹ� ���α׷��� ���
MVC ���Ͽ��� Controller ���� ��. start -> initialize -> service -> destroy

### spring-boot�� �ʱ����.
#### 1. spring boot �÷����� ��ġ
#### 2. �÷������� ��ġ�ϸ� spring intiaizr�� ����.
#### 3. �̰� �����ؼ� ������Ʈ ����.
#### 4. Web ���̺귯�� ����.
#### 5. SpringBoot�� ���ø����̼��� ���۵ɶ� �ʿ��� �⺻ �������� �ڵ����� �����ϰ� �Ǿ� �ִµ� (Auto Configuration) �� �� DataSource������ �ڵ����� �� �� �ʿ��� Database Type �������� �����Ǿ� ���� �ʾƼ� ������ ����.
#### 6. db�� �������� ���� ��� ���� Ŭ������ @EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class}) �߰�.
#### 7. SpringBoot�� ������Ʈ�� �����ɶ� Web���̺귯���� ���Ե� ���, ������ �����ҽ��� src > main > resources > static �Ʒ����� �����ǵ��� �����ȴ�. ��, html, css, js, image���� ������������ static�Ʒ��� ��ġ��Ű�� ���ٰ����ϰ�, static�� ��Ʈ������ �ȴٴ� �ǹ��̴�.������Ʈ�� ������ ���, ���̺귯�� �߰��Ҷ� Web ���̺귯�� �߰��ߴٸ� static ������ �ڵ����� ���������.
#### 7. Index.html�� �⺻�ε� �ϴ�. �⺻������ ��� �ٲٴ� �ɱ�?
#### 8. ��Ʈ�� �⺻�� 8080�ε� �ѵ� ��Ʈ�� ��� �ٲٴ� ���ϱ�?
> ��Ʈ�� application.properties���� server.port=num ���� �⺻ port�� �ٲ� �� �ִٰ� �Ѵ�.
#### 9. Controller Ŭ������ ����µ�, Ŭ������ ��������� ��ġ�� �߿��ϴ�. ������ ����ߵ��� ��������Ʈ�� ����Ŭ������ ������ ���� ������Ʈ��ĵ�� �Ѵٰ� �߾��µ�,��������Ʈ�� ������Ʈ ��ĵ�� �� ��, �⺻������ ����Ŭ������ �ִ� ��ġ�� �������� ��ĵ�� �ϰԵȴ�.����, AutoScan�� �Ǿ�� �ϴ� ������Ʈ Ŭ������ - ��ǥ������ @Controller, @Service, @Repository, @Component���� ��ġ�� ����Ŭ������ ��ġ�� ��Ű������  ���� ��Ű���� �ְų�, ������ �ƴ� �ٸ� ��Ű���� �ִ� ���, ��ĵ�� ���� �ʴ´�.

### SpringBoot�� MVC �⺻.
#### 1. view�� �⺻ - jsp�� ����ϱ� ���� �߿��� ����. (�̰� ������ ���� �����ߴ�)
>pom.xml��
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
        �� �߰��� �����.
        �׸��� �⺻ �������� spring.mvc.view.prefix=/WEB-INF/views/
          spring.mvc.view.suffix=.jsp ��ο� �ִ� .jsp������ �����ϰڴ� �ǹ�.
#### 2. controller�� �⺻.
> ���� ��Ű���� controller ������ ����� class ���� �߰�. @Controller �� ����� boot�� �ڵ����� component scan�� �� scan ��. ���� class @ComponentScan(basePackages = "com.example.demo") ���� ��� return "hello"�� �ϸ� �⺻�������� ������ prefix, suffix�� �پ� /WEB-INF/views/hello.jsp �� ����Ǵ� �����̴�.
@RestController�� �� ��ü�� ��ü�� �ǹǷ� �������� ����, return ���� �ٷ� html�� ���� ����̴�.
#### 3. Project Structure -> Facets ���� ��μ����� �������.

#### 4. MVC �����̶� �׷��� Ruby On rails, Node express�� ����Ѱ� ����, ��Ʈ������ ���� �ʴ´�.

### View ���ø��� ����.
#### 1. ������ ��Ʈ������ JSP�� �ǰ����� �ʾ�, Thymeleaf ���.
#### 2. xml�� thymeleaf�������� �� �������� �߰� �ߴ��� ������ �ۼ��� JSP���� �ڵ�� �۵����� ����. �Ƹ��� Overwrite�Ǵ� �� �ϴ�.
#### 3. thymeleaf�� ���� ���ؼ��� html�� ��ũ�� �߰������ ��.

### HTTP Method.
#### 1.@RequestMapping(value="/post",method=RequestMethod.POST) �̷������� GET, POST ����
> Express�� �� ������ ���� ���δ�.
#### 2. Post������� �Ѿ���� Parameter ó��.
> @RequestParam(value="id")Object id
#### 3. URI ���ø�. PathParameter�� ����.
> Express ������ '/post/:num' �� ���� path.parse(req.params.num).base; �� ���� ������ �޾ƿԾ����� Spring Boot������ value="/post/{num}"�� ���� @PathVariable int num �� ���� ������� �޾ƿ���, Ŭ���̾�Ʈ���� ������ �����ϴ°��� �� ���� ����. ���������� Node Express�� �� ���̰� ���� �Ҹ��� �� �ϴ�.


###Database MySQL ��������
#### 1. ������ ���̽� ���� create database;
#### 2. ���� ���� create user hy identified by '1234';
#### 3. ������ ���� �ο� grant all privileges on dbs.* to hy;
#### 4. flush.

###Database MySQL - SpringBoot ���� (With mybatis)
#### 1. maven �߰�.
#### 2. application.properties����
```
spring.datasource.url=jdbc:mysql://localhost:3306/dbs?useSSL=false
spring.datasource.username= �����̸�
spring.datasource.password= ��й�ȣ
```
> ����̹��� spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver�� ���������� ������ ��(����������Ʈ �����ε�)
#### 3. Mybatis �������� �ε�.
>mybatis.config-location=mybatis-config.xml
#### 4. �������� ����. <mapper resource="MemberMapper.xml"/>
#### 5. Mapper.xml ���Ͽ� �Լ����, �Լ������� ���� �ۼ�
```
<select id="selectMemberList" parameterType="com.example.demo.BoardDomain" resultType="com.example.demo.BoardDomain">
select * from board
</select>
```
#### 6. Mapper.java���Ͽ� interface�� ����� �Լ� ���
```
public interface BoardMapper {
    public List<BoardDomain> selectMemberList();
}
```
>�Լ��� ���� ���� �ڵ�� xml���Ϸ� �ۼ� ��.
#### 7. �������� ���߰� �Ӽ�, insert, delete �� �غ�����. multpart���ε嵵 �����غ��� �ڴ�.

### ������������ Multipart�� ����.
#### 1. Front���� �Ȱ���.
```
<form type="multipart....">
input multiple="multiple" type="file" name="...."...>
</form>
```
#### 2. ����Ʈ�� form�±׿��� file�±��� �̸����� ������ @RequestParam("userimage") List<MultipartFile> files parameter����.
#### 3. ���������� ������ ���ε� �� ��� ������ List�� ����.
#### 4. for���� �̿��Ͽ� �ϳ��� ���� �ø��� ������ ������ŭ �ݺ�.
#### 5. �ϳ� �ø��� ����.
#### 6. nodejs���� multer�� ������ ��������, ������� ����� ����ϴ°Ŷ� �׷��� �� ���ص��� �ʾ���.
#### 7. ���������� ������ �� ���, �ϴ� ���, �̸����� �� ������ �ϳ� ����� �Է¹��� multipart������ ���� �� ���Ͽ� ����� ���ε� ��.
#### 8.
```
String sourceFileName = files.get(i).getOriginalFilename();
            String sourceFileNameExtension = FilenameUtils.getExtension(sourceFileName).toLowerCase();
            ���� �̸��� �޿Ϳͼ� ������ �̸����� ����
            String fileUrl = "/Users/HY/IdeaProjects/demo/src/main/webapp/WEB-INF/uploadFiles/";
            destinationFileName = RandomStringUtils.randomAlphanumeric(32) + "." + sourceFileNameExtension;
            destinationFile = new File(fileUrl + destinationFileName);]
            ������ ���� ��� + �����ϰ� ������ �̸����� ���� ����.
```
#### 9.multipart������ �����Ͽ� �����.
```
destinationFile.getParentFile().mkdirs();
               files.get(i).transferTo(destinationFile);
```
#### 10. post������� �Ѿ�� ���� ó���� ����.
>parameter�� HttpServletRequest request�� �����ϰ�, equest.getParameter("id")���� ������ �޾ƿ��� �ȴ�.
��û �밡�� �ٴ°ɷ� �˰� �־��µ�, ���ο�� �����.

#### 11. �������� ���ε�, �����ͺ��̽� ������� ���� ������, ���� CRUD�� ����� ���߰ڴ�. ����, facebook OAUTH, �̸��� ������� ���� �����غ���.

### ORM(Object Relation Mapping)�� ����
#### ��ü�� �����ͺ��̽� ����ġ ������ �ذ��ϱ� ���� ����.
#### MyBatis, JPA. MyBatis�� ���� ������ JPA�� ���� ���� �߼���� �Ѵ�.
#### �������� MyBatis�� ����Ҷ��� mapperŬ����, �׸� ���� xml, mybatis������ ���� xml���� �� ������ ���� ����������, JPA�� ���� ������ ���� �� ������ ����.
#### relation�� Mapping�� ���� class(model), �׸� �����ϴ� Repositry interface �� �����ϸ�, JPA���� �⺻���� �����ϴ� �Լ��� �� �� �־� ���ϴ�.
#### ���� mybatis���� query mapping�� �ϴ� ��ɵ� ����� ������ �ϴ� JPA�� ���ٰ� ���� �ȴ�.

### JPA ����� ���� ����.
#### @Entity�� Ŭ������ �����ͺ��̽� ���̺��� �����ϴ� ������ �Ѵ�.
#### @Repository�� Entity���ۿ� �ʿ��� ������ �޼���ȭ �ؼ� ����� �� �ִ� ������ �Ѵ�.
#### ��������
> 1:1, 1:N, N:1, N:N @ManyToOne, @OneToMany
> @ManyToOne�� ��� �ε��� �⺻���̴�. ��� �ε����� ����� ���� ����� ��ƼƼ �������� �ѹ��� ���������� �ϹǷ� ���ɿ� ������ ���� �� �ִ�. �����ε� �ǵ��� �����ϴ°��� ����
. @ManyToOne(fetch = FetchType.LAZY)
> @OneToMany�� ����� ��� mappedBy�� ���� ������ ������ش�. @OneToMany(mapperBy = "school")
#### Repository.save(new entity)������ insert������ ����. �������� update�� ����.
#### @AutoWired -> ������ ����. Repository����Ҷ� ����Ѵ�.


#### 1. Relation�� Mapping�� ���� Model Ŭ���� ����
> @Entity Anotation�� �ٿ���� ��.
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
#### 2. ����� ���� Repository Ŭ���� ����.
> @Repository Annotation�� �ٿ���� ��.
```
@Repository
public interface BoardRepository extends JpaRepository<board, Long> {

    board findByusername(@Param("username")String username);
}
```
#### 3. ����� Controller���� Autowierd���� �� ���(������ ����)
```
@Autowired
  BoardRepository BoardRepository;
```
#### 4. JPA���� �����ϴ� �⺻���� CRUD�Լ�.
```
��ȯŸ�� findBy�ʵ��(Parameter);
board findByusername(@Param("username")String username);
```

#### 5. @Query Annotation�� ����� �Լ��� ���� �� �ִ�. ���� JPQL�� �ۼ��Ͽ��� �ϸ�, ��Ī�� �ʼ��� ����Ͽ����Ѵ�. (�� �κж����� �����ɸ�)
```
 SELECT m FROM Member AS m where m.username = 'HY'
 ��Ī�� �����ϴ� AS�� ���� �����ϴ�.
 @Query("select u from board u where u.username = :myname")
    List<board> customfunc(@Param("myname") String name);
 ```
 > @Param �� �۵����� �ʾ� ������ ��� �Ͽ���. �˰��� mybatis���� jpa�� �ٲٴ� �߿� @Param�� mybatis��Ű������ �޾ƿͼ� ��� ������ ���� ���̾���... ��Ű���� �ٲ��ִ� �ٷ� �ذ� �Ǿ���.. ���� �㹫�ϴ�.

 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
<img width="809" alt="2018-09-30 7 27 11" src="https://user-images.githubusercontent.com/37579650/46257612-bbb57e00-c4f7-11e8-99dd-ea79d445a24a.png">
<img width="807" alt="2018-09-30 7 27 17" src="https://user-images.githubusercontent.com/37579650/46257613-bbb57e00-c4f7-11e8-94c5-a9c4fed5445a.png">

### 6. @Modifying, @Query�� �̿��� Į�� �Ӽ��� �ٲٴ� �Լ��� �ۼ��ϴ�
```
@Modifying
    @Query("update user_schema s set s.auth=1 where s.id=?1")
    void Authuser(@Param("id")String id);

javax.persistence.TransactionRequiredException: Executing an update/delete query
```

### ������ �߻��Ͽ���. ������ ã�� ���ϰڴ�.
> @Modifying �Ӹ��ƴ϶� @Transactional ������̼ǵ� �߰��� �ۼ��ϴ� �۵��Ͽ���.
�̰Ͷ����� ���� ����Ѱ� ����. @Transactional ������̼��� ���������� �ϴ��� �˾ƺ��� �ڴ�.
>@Transactional�� �̸����� �� �� �ֵ��� Transaction�� �����ִ� ���̶�� �Ѵ�. DB�ð��� ��� Ʈ����ǰ� �Ȱ��� ���̴�. �� ������ ����, �������� ����... Modifying�� ��

##JPA
JPA�� ������� ������ ����.
jdbc�� �������.
Query�� ��κ� ��������� �ٸ��͵� ����.
�ݺ����� �ڵ尡 ����.
�������� ������ �ذ��ϱ� ���� ORM���
spring boot������ Hikari ���

������ �� ��� ���.
��ü������ ������ Ȱ���ϱ� ����.
���� ����������
�ڵ� ����
����Ͻ� ���� ���� �� �׽�Ʈ ����
ORM�̶� ���ø����̼��� Ŭ������ sql�����ͺ��̽��� ���̺� ������ ���� ������ ����� ��Ÿ�����͸� ����Ͽ� ��ü�� sql�����ͺ��̽��� ���̺� �ڵ����� ����ȭ ���ִ� ���

hibernate�� db������ �˸´� sql�� �ٲ���

���̺�� ���̺��� �ܷ�Ű�� �� �ٸ����̺��� ��Ű�� �ܷ�Ű�� ����. �ٸ� �� ���̺��� �ܷ�Ű���� �Ұ�.

@Entity �� Ŭ������ �����ͺ��̽��� ~��� ���̺� �����̵Ǵ� Ŭ������.
@id : ��Ű�� ����
@GenteratedValue: �ڵ����� �����Ǵ� ���� ����ϰڴ�. db�� �̹� ���̺��� ������� �ְ�, �� ���� ����Ҷ��� IDENTITY

spring.jpa.hibernate.ddl-auto=update, ������Ʈ , create �� �ϸ� �Ź� ����� ���Ӱ� ����°��̴�.
> Entity class�� �Ӽ� �߰��ϸ� relation�� �ڵ����� �߰��ȴ�.

@Entity ����
Annotation ��� ����
@Entity�� �ڵ����� ���̺�� ���� ��ǻ� @Table Annotation�� �����Ǿ� ����. �⺻������ Ŭ���� �̸��� ������ ��ƼƼ ���
@Entity(name="sdasad")���� ��ƼƼ ���� ����
@Table���� ����ϴ� �⺻ ���� Entity�� �̸��̴�. �ƹ��� ������ ���� ������ �⺻������ Ŭ�����̸��� ���� entity����.


db���� UserŰ���尡 �־ ����� �� ����. @Entitiy(name = "fdsafsd") �� ������ ���εǴ� �����̼��� ������ �ٲٴ� ���� �ƴ϶�, ���� Entity Ŭ������ �̸��� ������ �ִ°�. ��ƼƼ �̸��� �̿Ͱ��� ����� ���� �ٲ� �� �ִ�.

@Column(nullable = false, unique = true);

@Temporal ������̼�
```
@Temproal(TemporalType.TIMESTAMP)���� �����ϸ� ��¥ �ð�,
@Temproal(TemporalType.TIME) - > �ð���.

@Transient �� �߰��ϸ� column���� ������ �ʴ´�
```

@Transient
private String no; ��� �ϸ� ���̺� no �Ӽ��� �߰����� �ʴ´�

Class ->  Entity Type
vairable -> Value Type

�⺻������ db���� ������ ����°��� �ƴ϶� JAP�� EntityŬ������ �����ϸ� DB�� ���̺��� �����ȴ�.

ValueŸ�� ����.
@Embadable ������̼� ����Ͽ� Ŭ���� �ϳ� ����, �� Ŭ������ value�� ���� Ŭ��������

private Adress temp ��� �����ϸ� Address Ŭ������ ��Ұ� db���̺��� �Ӽ����� �߰��ȴ�.

```
@Embeded
@AttributePverrodes({
  @AttributePverride(name="street", column=@Column(name="home_street") )
  })
```
  private Address adress�� �������̵� �ؼ� ��� ����. Address�� street ��Ұ� home_street��� �̸����� ������ �ȴ�.

  1��� ���� @OneToMany
  � ��ƼƼ�� �ְ� �ٸ� ��ƼƼ�� �ִ�.
  ����� �׻� �ΰ��� ��ƼƼ�� �¹��� �ִ�.

  �Ӽ��� collection�� �ƴ����� one

  Owner ���̺��� �ܷ�Ű�� �����ϰ� �����ְ� �ȴ�. �� �ܷ�Ű�� ��� ��ƼƼ�� id�� �����Ѵ�.

  ������� ���� �̶�°� ���踦 ���������� �� ���� �ݿ��� �Ǵ°�.

@ManyToOne�� �ܷ�Ű�� �߰��ϴ� �ݸ�
@OneToMany�� �������̺��� ���� �����. �� ���̺� ���迡 ���� ������ ����Ǹ� �ܷ�Ű�� ���� �������� �ʴ´�.

���� �����ϴ� ����� ���踦 ���� ���� �ִ�. ���ʿ� OneToMany, ManyToOne�� �����ϸ� ����� �����̶�� ������ �� ������ �̰��� �ΰ��� �ܹ��� �����̴�. ����� ���踦 �����Ϸ��� ���� ������ ������Ѵ�. ����� ���踦 �����Ϸ���
@OneToMany(mappedBy = "owner")�� ���� �ؾ��ϸ� mappedBy �� OneToMany�ʿ� ����.
�̶� ���踦 �����ÿ� ���ʿ� �Ѵ� ���踦 ������ �־�� �Ѵ�. @OneToMany�� �ʿ� .add.. �� ���ְ� @ManyToOne�� setOwner������ �������� �������־�� ���������� ���� �����̵�. ����� �����ε� ���ʿ��� addȤ�� set ���شٴ°� �����ʴ°�. add�� �ʼ������� �����ؾ��ϴ� �ڵ�� �ƴϴ�. ������ ��ü���������� ���������� �Ѵ� �ϴ°��� ����.

�̻����� ���� Convenient method�� ����� ����ϴ� ��.
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

Entity�� ���� Cascade Option.
@OneToMany, @ManyToOne�� Cascade �ɼ��� �ִ�.
cascade�� entity�� ���º�ȭ�� ���̽�Ű�� ��.
���´� ũ�� 4������ �ִ�. Transient Removed Persistant Detached
Transient : ��ü�� db�� ������� �ȵ��� jpa, hibernate�� ���� �𸣴� ����. save�ϱ� ��.
SAVE�� �ϸ� persistent���°� �ȴ�. save�� �Ѵٰ� ��ü�� �ٷ� ���� ���� �ƴϴ�. �� ���·� �����ϰ� �ִٰ� ���� ������ db�� �־�� �ڴ�. �Ǵ��ϴ� �� ������ �����ϰ� �ȴ�. save�� ȣ���ߴٰ� �ؼ� �� ��� insert ������ �߻��ϴ� ���� �ƴϴ�. save�� ȣ���ϸ� hibernate�� �ƴ� ���� persistant 1��ĳ��. �ν��Ͻ��� cache�� �� ����. �̻��¿��� �ٽ��ѹ� �� �ν��Ͻ��� �޶�� �ϸ� ����Ʈ ������ �߻����� �ʴ´�. cache�ϰ� �ִ°� �ٰ� �ϸ� �ش�. db���� �����°��� �ƴ�. ������ ������ ���� ���¿��� �ִ°�. transaction�� ������ �� commit�� �Ͼ��, insert������ �߻��Ѵ�. -> �߰��� ���� �ٲٴµ� ���ʿ��� �׼��� ������ �ʴ� ����. ��ü�� ��� �����ϰ� �ִٰ� Ʈ������� ������ ���� ����. ( Dirty checking �� ��ü�� ��������� ��� �����Ѵ�.)

removed���¿� �ӹ��� �ִٰ� commit�� �Ͼ�� �����Ѵ�.

 hibernate�� persistant ���·� �����ϰ� �ִ�.
@OneToMany(cascade =  )

������� �Խñ۰� ����� ����. �Խñ��� �����Ǹ� ��۵� �����Ǿ�� �Ѵ�.
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

@OneToMany(cascade =CascadeType.PERSIST)�� ������ �ϸ�. post.save()�� ������ �Ҷ� �� persistant�� �˷��ּ���. transient���� �Ѿ�� ���� persistant���ǰ� ������ �ȴ�. CascadeType.REMOVE ������ ���ﶧ ����Ʈ�� �����ϴ¼��� removed���°� ���İ� �ǰ� comment�� removed���°� �ż� ���� �����ش�. �׳� CASCADETYE.ALL�� ���� �����ϵ��� �����ϸ� ���ϴ�.
```

Fetch ���������� ��ƼƼ�� ��� �����ð��ΰ�. ��(Eager?) ���߿�(Lazy?) .

OneToMany�� �⺻������ Lazy �����ϱ�.
ManyToOne�� �⺻������ Eager. �����غ��� �ո����̴�.

�� default���� lazy�� ����, ������� post�� �����ִ� comment�� �����ö� n+1����Ʈ ������ ����� �ִ�. �̷� fetch������ �� ���ϴ°� ���ɿ� ū ������ ��ħ.

������ ������ JPA.
data access object ������ �ϴ� repository�� ����.

```
@Repository
@Transactional
public class PostRepository{

  @AutoWired ����
  @PersisenceContext�� ���°� ����.
  ������ �ڵ带 �ִ��� ���ߴ°� JPA�� ��Ģ�̶�..
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
�̷��� �� ���� �ʴ´�.
```

�ξ� ���� ���. �ֱٿ� ���� ������ ����

```
@Repository
public interface PostRepository extends JpaRepository<Post, Long>{


}
```

������ @EnableJpaRepositories�� �ٿ��� �ϴµ� @SpringBootApplication�� �ڵ����� ���� �� �ش�.

������ ������� ?�� ��Ÿ���� ���� ���� ���. ���� Ȯ�ξ��ϰ� �ҰŸ� hibernate�� ��������. ���ɿ� ������ ���� �� �ִ�.
```
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=TransactionRequiredException
loggin.level.org.hibernate.type.descriptor.sql=trace
```

SpringData Common
��ӹ޾Ƽ� Interface�� ���� JpaRepository�� Repository(��� x), CrudRepository, PagingAndSortingRepository //������������ Common// ���� ����� �� �߰��Ѱ�.

�̷��� �͵��� @NoRepositoryBean Annotation�� �پ��־� ���� ���� ����ϴ°��� �����Ѵ�. (�̰��� ��ӹ޾� ����϶�� ��. �߰��ܰ� Repository, ���� Repository�� �ƴ��� �ǹ�)

CrudRepository : Save, SaveAll, findById, existsById(�������� �Ǵ�), findAll, findAllById

@Test�� ���� ������ ��� rollback�̱� ������ hibernate�� ������ ������ ������ �ʴ´�.

PagingAndSortingRepository : findAll(Pageable page)
postRepository.findAll(PageRequest.of(0,10)) new PageRequest ���� PageRequest.of�� �ٲ�. deprecated�� �߻��Ѵ�.

nulló��
Optional�� null�� ����. isEmpty���.

Query�����
�⺻���� naming ��Ģ���� �Լ����, ���� ������� �Ҷ��� @Query Annotation ����. ��Ģ ����.

Like�� ����� ����� �ϴ� Contain�� �ִ�.
findByCommentContains�� ���� ��� ���� -> �̿Ͱ��� ����ϸ� Like Query�� �߻��Ѵ�.

Async ������̼��� ����ϸ� �񵿱�� ó������.������ ����ȭ �Ϸ��� �񵿱� ó������, ������ ����ȭ �ϴ°��� ���ɰ����� �� ����.
�񵿱� ������ ������ �Ⱦ��°��� ����

Custom Repository 
���̻�� Impl ���̴� ���� ������.
Ŀ���� '�������̽�'�� �����, �׵ڿ� Impl�̶�� ���̻縦 ���� '����ü'�� �����Ѵ�. Impl�� �����Ǿ� �ֱ� ������ ������ Impl�� �����

Insert �ڿ� Select Delete�� �ִ� ���, Select�� ������ ������ �߻����� ������ Select�� �ִ°�� Insert�� Select�� ������ �� �� �����Ƿ� Insert������ �߻���.

�����ͺ��̽��� delete ��ũ ���ϴ� ���� : ������ �ѹ� �����̱� ������ delete ���� �߻����� ����.
