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
#### 9. Controller Ŭ������ ����µ�, Ŭ������ ��������� ��ġ�� �߿��ϴ�. ������ ����ߵ��� ��������Ʈ�� ����Ŭ������ ������ ���� ������Ʈ��ĵ�� �Ѵٰ� �߾��µ�,��������Ʈ�� ������Ʈ ��ĵ�� �� ��, �⺻������ ����Ŭ������ �ִ� ��ġ�� �������� ��ĵ�� �ϰԵȴ�.����, AutoScan�� �Ǿ�� �ϴ� ������Ʈ Ŭ������ - ��ǥ������ @Controller, @Service, @Repository, @Component��-�� ��ġ�� ����Ŭ������ ��ġ�� ��Ű������  ���� ��Ű���� �ְų�, ������ �ƴ� �ٸ� ��Ű���� �ִ� ���, ��ĵ�� ���� �ʴ´�. ��ó: http://yonguri.tistory.com/entry/��������Ʈ-SpringBoot-����ȯ��-����-2-MVC-ȯ�汸�� [Yorath's ��α�]

### SpringBoot�� MVC �⺻.
#### 1. view�� �⺻ - jsp�� ����ϱ� ���� �߿��� ����. (�̰� ������ ���� �����ߴ�)
>pom.xml�� <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
        </dependency>
        <dependency>
            <groupId>org.apache.tomcat.embed</groupId>
            <artifactId>tomcat-embed-jasper</artifactId>
            <scope>provided</scope>
        </dependency> �� �߰��� �����.
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
#### 2. application.properties���� spring.datasource.url=jdbc:mysql://localhost:3306/dbs?useSSL=false
spring.datasource.username= �����̸�
spring.datasource.password= ��й�ȣ
> ����̹��� spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver�� ���������� ������ ��(����������Ʈ �����ε�)
#### 3. Mybatis �������� �ε�.
>mybatis.config-location=mybatis-config.xml
#### 4. �������� ����. <mapper resource="MemberMapper.xml"/>
#### 5. Mapper.xml ���Ͽ� �Լ����, �Լ������� ���� �ۼ� <select id="selectMemberList" parameterType="com.example.demo.BoardDomain" resultType="com.example.demo.BoardDomain">
        select * from board
    </select>
#### 6. Mapper.java���Ͽ� interface�� ����� �Լ� ��� public interface BoardMapper {
    public List<BoardDomain> selectMemberList();
}
>�Լ��� ���� ���� �ڵ�� xml���Ϸ� �ۼ� ��.
#### 7. �������� ���߰� �Ӽ�, insert, delete �� �غ�����. multpart���ε嵵 �����غ��� �ڴ�.

### ������������ Multipart�� ����.
#### 1. Front���� �Ȱ���. <form type="multipart....">
<input multiple="multiple" type="file" name="...."...>
</form>
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
```
            ���� �̸��� �޿Ϳͼ� ������ �̸����� ����
            ~~~
            String fileUrl = "/Users/HY/IdeaProjects/demo/src/main/webapp/WEB-INF/uploadFiles/";
            destinationFileName = RandomStringUtils.randomAlphanumeric(32) + "." + sourceFileNameExtension;
            destinationFile = new File(fileUrl + destinationFileName);
            ~~~
            ������ ���� ��� + �����ϰ� ������ �̸����� ���� ����.
#### 9.multipart������ �����Ͽ� �����.
~~~
destinationFile.getParentFile().mkdirs();
               files.get(i).transferTo(destinationFile);
~~~
#### 10. post������� �Ѿ�� ���� ó���� ����.
>parameter�� HttpServletRequest request�� �����ϰ�, equest.getParameter("id")���� ������ �޾ƿ��� �ȴ�.
��û �밡�� �ٴ°ɷ� �˰� �־��µ�, ���ο�� �����.

#### 11. �������� ���ε�, �����ͺ��̽� ������� ���� ������, ���� CRUD�� ����� ���߰ڴ�. ����, facebook OAUTH, �̸��� ������� ���� �����غ���.
