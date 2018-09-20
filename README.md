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
#### 2. controller�� ��.
> ���� ��Ű���� controller ������ ����� class ���� �߰�. @Controller �� ����� boot�� �ڵ����� component scan�� �� scan ��. ���� class @ComponentScan(basePackages = "com.example.demo") ���� ��� return "hello"�� �ϸ� �⺻�������� ������ prefix, suffix�� �پ� /WEB-INF/views/hello.jsp �� ����Ǵ� �����̴�.
#### 3. Project Structure -> Facets ���� ��μ����� �������. 

#### 4. MVC �����̶� �׷��� Ruby On rails, Node express�� ����Ѱ� ����, ��Ʈ������ ���� �ʴ´�.
