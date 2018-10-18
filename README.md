# TIL-Spring_boot
Today i learned about spring-boot

### ¼­ºí¸´ ÀÌ¶õ
> À¥ÇÁ·Î±×·¡¹Ö¿¡¼­ Å¬¶óÀÌ¾ğÆ®ÀÇ ¿äÃ»À» Ã³¸®ÇÏ°í ±× °á°ú¸¦ ´Ù½Ã Å¬¶óÀÌ¾ğÆ®¿¡°Ô Àü¼ÛÇÏ´Â Servlet Å¬·¡½ºÀÇ ±¸Çö ±ÔÄ¢À» ÁöÅ² ÀÚ¹Ù ÇÁ·Î±×·¡¹Ö ±â¼ú
MVC ÆĞÅÏ¿¡¼­ Controller °°Àº °Í. start -> initialize -> service -> destroy

### spring-boot·Î ÃÊ±â¼ÂÆÃ.
#### 1. spring boot ÇÃ·¯±×ÀÎ ¼³Ä¡
#### 2. ÇÃ·¯±×ÀÎÀ» ¼³Ä¡ÇÏ¸é spring intiaizr°¡ »ı±è.
#### 3. ÀÌ°É ¼±ÅÃÇØ¼­ ÇÁ·ÎÁ§Æ® »ı¼º.
#### 4. Web ¶óÀÌºê·¯¸® ¼±ÅÃ.
#### 5. SpringBoot´Â ¾îÇÃ¸®ÄÉÀÌ¼ÇÀÌ ½ÃÀÛµÉ¶§ ÇÊ¿äÇÑ ±âº» ¼³Á¤µéÀ» ÀÚµ¿À¸·Î ¼³Á¤ÇÏ°Ô µÇ¾î ÀÖ´Âµ¥ (Auto Configuration) ±× Áß DataSource¼³Á¤ÀÌ ÀÚµ¿±¸¼º µÉ ¶§ ÇÊ¿äÇÑ Database Type Á¤º¸µéÀÌ ¼³Á¤µÇ¾î ÀÖÁö ¾Ê¾Æ¼­ ¿¡·¯°¡ ³­´Ù.
#### 6. db¸¦ °áÁ¤ÇÏÁö ¾ÊÀº °æ¿ì ¸ŞÀÎ Å¬·¡½º¿¡ @EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class}) Ãß°¡.
#### 7. SpringBoot´Â ÇÁ·ÎÁ§Æ®°¡ »ı¼ºµÉ¶§ Web¶óÀÌºê·¯¸®°¡ Æ÷ÇÔµÈ °æ¿ì, Á¤ÀûÀÎ À¥¸®¼Ò½º´Â src > main > resources > static ¾Æ·¡¿¡¼­ °ü¸®µÇµµ·Ï ¼³Á¤µÈ´Ù. Áï, html, css, js, imageµîÀÇ Á¤ÀûÄÁÅÙÃ÷´Â static¾Æ·¡¿¡ À§Ä¡½ÃÅ°¸é Á¢±Ù°¡´ÉÇÏ°í, staticÀÌ ·çÆ®Æú´õ°¡ µÈ´Ù´Â ÀÇ¹ÌÀÌ´Ù.ÇÁ·ÎÁ§Æ®¸¦ »ı¼ºÇÒ ´ç½Ã, ¶óÀÌºê·¯¸¦ Ãß°¡ÇÒ¶§ Web ¶óÀÌºê·¯¸¦ Ãß°¡Çß´Ù¸é static Æú´õ°¡ ÀÚµ¿À¸·Î ¸¸µé¾îÁø´Ù.
#### 7. Index.htmlÀÌ ±âº»ÀÎµí ÇÏ´Ù. ±âº»¼³Á¤Àº ¾î¶»°Ô ¹Ù²Ù´Â °É±î?
#### 8. Æ÷Æ®´Â ±âº»ÀÌ 8080ÀÎµí ÇÑµ¥ Æ÷Æ®´Â ¾î¶»°Ô ¹Ù²Ù´Â °ÍÀÏ±î?
> Æ÷Æ®´Â application.properties¿¡¼­ server.port=num À¸·Î ±âº» port¸¦ ¹Ù²Ü ¼ö ÀÖ´Ù°í ÇÑ´Ù.
#### 9. Controller Å¬·¡½º¸¦ ¸¸µå´Âµ¥, Å¬·¡½º°¡ ¸¸µé¾îÁö´Â À§Ä¡°¡ Áß¿äÇÏ´Ù. À§¿¡¼­ ¾ğ±ŞÇßµíÀÌ ½ºÇÁ¸µºÎÆ®´Â ¸ŞÀÎÅ¬·¡½ºÀÇ ¼³Á¤¿¡ ÀÇÇØ ÄÄÆ÷³ÍÆ®½ºÄµÀ» ÇÑ´Ù°í Çß¾ú´Âµ¥,½ºÇÁ¸µºÎÆ®´Â ÄÄÆ÷³ÍÆ® ½ºÄµÀ» ÇÒ ¶§, ±âº»ÀûÀ¸·Î ¸ŞÀÎÅ¬·¡½º°¡ ÀÖ´Â À§Ä¡¸¦ ±âÁØÀ¸·Î ½ºÄµÀ» ÇÏ°ÔµÈ´Ù.¸¸¾à, AutoScanÀÌ µÇ¾î¾ß ÇÏ´Â ÄÄÆ÷³ÍÆ® Å¬·¡½ºµé - ´ëÇ¥ÀûÀ¸·Î @Controller, @Service, @Repository, @ComponentµîÀÇ À§Ä¡°¡ ¸ŞÀÎÅ¬·¡½º°¡ À§Ä¡ÇÑ ÆĞÅ°Áöº¸´Ù  »óÀ§ ÆĞÅ°Áö¿¡ ÀÖ°Å³ª, ÇÏÀ§°¡ ¾Æ´Ñ ´Ù¸¥ ÆĞÅ°Áö¿¡ ÀÖ´Â °æ¿ì, ½ºÄµÀÌ µÇÁö ¾Ê´Â´Ù.

### SpringBootÀÇ MVC ±âº».
#### 1. viewÀÇ ±âº» - jsp¸¦ »ç¿ëÇÏ±â À§ÇÑ Áß¿äÇÑ ¼³Á¤. (ÀÌ°Í ¶§¹®¿¡ ÇÑÂü »ğÁúÇß´Ù)
>pom.xml¿¡
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
        ¸¦ Ãß°¡Çì Áà¾ßÇÔ.
        ±×¸®°í ±âº» ¼³Á¤À¸·Î spring.mvc.view.prefix=/WEB-INF/views/
          spring.mvc.view.suffix=.jsp °æ·Î¿¡ ÀÖ´Â .jspÆÄÀÏÀ» ½ÇÇàÇÏ°Ú´Ü ÀÇ¹Ì.
#### 2. controllerÀÇ ±âº».
> °°Àº ÆĞÅ°Áö¿¡ controller Æú´õ¸¦ ¸¸µé°í class ÆÄÀÏ Ãß°¡. @Controller ¸¦ ÇØÁà¾ß boot°¡ ÀÚµ¿À¸·Î component scanÇÒ ¶§ scan ÇÔ. ¸ŞÀÎ class @ComponentScan(basePackages = "com.example.demo") ¿¹¸¦ µé¾î return "hello"¸¦ ÇÏ¸é ±âº»¼³Á¤¿¡¼­ ÁöÁ¤ÇÑ prefix, suffix°¡ ºÙ¾î /WEB-INF/views/hello.jsp °¡ ½ÇÇóµÇ´Â ±¸Á¶ÀÌ´Ù.
@RestController´Â ±× ÀÚÃ¼°¡ ¸öÃ¼°¡ µÇ¹Ç·Î ºäÆäÀÌÁö ¾øÀÌ, return À¸·Î ¹Ù·Î htmlÀ» ¶ç¿ì´Â ¹æ½ÄÀÌ´Ù.
#### 3. Project Structure -> Facets ¿¡¼­ °æ·Î¼³Á¤µµ ÇØÁà¾ßÇÔ.

#### 4. MVC ÆĞÅÏÀÌ¶ó ±×·±Áö Ruby On rails, Node express¿Í ºñ½ÁÇÑ°Å °°¾Æ, ½ºÆ®·¹½º¸¦ ¹ŞÁø ¾Ê´Â´Ù.

### View ÅÛÇÃ¸´¿¡ ´ëÇØ.
#### 1. ½ºÇÁ¸µ ºÎÆ®¿¡¼­´Â JSP¸¦ ±Ç°íÇÏÁö ¾Ê¾Æ, Thymeleaf »ç¿ë.
#### 2. xml¿¡ thymeleafÀÇÁ¸¼ºÀ» ¸Ç ¸¶Áö¸·¿¡ Ãß°¡ Çß´õ´Ï ±âÁ¸¿¡ ÀÛ¼ºÇÑ JSP°ü·Ã ÄÚµå´Â ÀÛµ¿ÇÏÁö ¾ÊÀ½. ¾Æ¸¶µµ OverwriteµÇ´Â µí ÇÏ´Ù.
#### 3. thymeleaf¸¦ ¾²±â À§ÇØ¼­´Â html¿¡ ¸µÅ©¸¦ Ãß°¡ÇØÁà¾ß ÇÔ.

### HTTP Method.
#### 1.@RequestMapping(value="/post",method=RequestMethod.POST) ÀÌ·±½ÄÀ¸·Î GET, POST Á¶Àı
> Express¿Í º° Â÷ÀÌÁ¡ ¾ø¾î º¸ÀÎ´Ù.
#### 2. Post¹æ½ÄÀ¸·Î ³Ñ¾î¿À´Â Parameter Ã³¸®.
> @RequestParam(value="id")Object id
#### 3. URI ÅÛÇÃ¸´. PathParameter¿¡ ´ëÇØ.
> Express ¿¡¼­´Â '/post/:num' ¿¡ ´ëÇØ path.parse(req.params.num).base; °ú °°Àº ½ÄÀ¸·Î ¹Ş¾Æ¿Ô¾úÀ¸³ª Spring Boot¿¡¼­´Â value="/post/{num}"¿¡ ´ëÇØ @PathVariable int num ¿Í °°Àº ¹æ½ÄÀ¸·Î ¹Ş¾Æ¿À¸ç, Å¬¶óÀÌ¾ğÆ®¿¡¼­ ¼­¹ö·Î Àü¼ÛÇÏ´Â°ÍÀº º° Â÷ÀÌ ¾øÀ½. ¾ÆÁ÷±îÁö´Â Node Express¿Í º° Â÷ÀÌ°¡ ¾ø¾î ÇÒ¸¸ÇÑ µí ÇÏ´Ù.


###Database MySQL °èÁ¤»ı¼º
#### 1. µ¥ÀÌÅÍ º£ÀÌ½º »ı¼º create database;
#### 2. °èÁ¤ »ı¼º create user hy identified by '1234';
#### 3. °èÁ¤¿¡ ±ÇÇÑ ºÎ¿© grant all privileges on dbs.* to hy;
#### 4. flush.

###Database MySQL - SpringBoot ¿¬°á (With mybatis)
#### 1. maven Ãß°¡.
#### 2. application.properties¼³Á¤
```
spring.datasource.url=jdbc:mysql://localhost:3306/dbs?useSSL=false
spring.datasource.username= °èÁ¤ÀÌ¸§
spring.datasource.password= ºñ¹Ğ¹øÈ£
```
> µå¶óÀÌ¹ö´Â spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver¸¦ ¾²Áö¾ÊÀ¸¸é ¿¡·¯°¡ ³²(¹öÀü¾÷µ¥ÀÌÆ® °ü·ÃÀÎµí)
#### 3. Mybatis ¼³Á¤ÆÄÀÏ ·Îµå.
>mybatis.config-location=mybatis-config.xml
#### 4. ¼³Á¤ÆÄÀÏ »ı¼º. <mapper resource="MemberMapper.xml"/>
#### 5. Mapper.xml ÆÄÀÏ¿¡ ÇÔ¼öµî·Ï, ÇÔ¼ö¿¡µû¸¥ Äõ¸® ÀÛ¼º
```
<select id="selectMemberList" parameterType="com.example.demo.BoardDomain" resultType="com.example.demo.BoardDomain">
select * from board
</select>
```
#### 6. Mapper.javaÆÄÀÏ¿¡ interface·Î »ç¿ëÇÒ ÇÔ¼ö µî·Ï
```
public interface BoardMapper {
    public List<BoardDomain> selectMemberList();
}
```
>ÇÔ¼ö¿¡ µû¸¥ ³»ºÎ ÄÚµå´Â xmlÆÄÀÏ·Î ÀÛ¼º ÇÔ.
#### 7. ´ÙÀ½¿¡´Â ´ÙÁß°ª ¼Ó¼º, insert, delete µµ ÇØº¼¿¹Á¤. multpart¾÷·Îµåµµ ±¸ÇöÇØºÁ¾ß °Ú´Ù.

### À¥¿¡¼­ºÎÅÍÀÇ Multipart¿¡ ´ëÇØ.
#### 1. Front´ÜÀº ¶È°°À½.
```
<form type="multipart....">
input multiple="multiple" type="file" name="...."...>
</form>
```
#### 2. ÇÁ·ĞÆ®´Ü formÅÂ±×¿¡¼­ fileÅÂ±×ÀÇ ÀÌ¸§À¸·Î ¼­¹ö¿¡ @RequestParam("userimage") List<MultipartFile> files parameter¼±¾ğ.
#### 3. »çÁøÆÄÀÏÀ» ¿©·¯°³ ¾÷·Îµå ÇÒ °æ¿ì ¶§¹®¿¡ List·Î ¼±¾ğ.
#### 4. for¹®À» ÀÌ¿ëÇÏ¿© ÇÏ³ªÀÇ »çÁø ¿Ã¸®´Â °úÁ¤À» °¹¼ö¸¸Å­ ¹İº¹.
#### 5. ÇÏ³ª ¿Ã¸®´Â °úÁ¤.
#### 6. nodejs¿¡¼­ multer·Î ±¸ÇöÇØ º¸¾ÒÀ¸³ª, ¸¸µé¾îÁø ¸ğµâÀ» »ç¿ëÇÏ´Â°Å¶ó ±×·±Áö Àß ÀÌÇØµÇÁö ¾Ê¾ÒÀ½.
#### 7. ½ºÇÁ¸µ¿¡¼­ ±¸ÇöÇØ º» °á°ú, ÀÏ´Ü °æ·Î, ÀÌ¸§À¸·Î ºó ÆÄÀÏÀ» ÇÏ³ª ¸¸µé°í ÀÔ·Â¹ŞÀº multipartÆÄÀÏÀ» ¸¸µç ºó ÆÄÀÏ¿¡ µ¤¾î¾²´Â ½ÄÀÎµí ÇÔ.
#### 8.
```
String sourceFileName = files.get(i).getOriginalFilename();
            String sourceFileNameExtension = FilenameUtils.getExtension(sourceFileName).toLowerCase();
            ÆÄÀÏ ÀÌ¸§À» ¹Ş¿Í¿Í¼­ ÀûÀıÇÑ ÀÌ¸§À¸·Î º¯°æ
            String fileUrl = "/Users/HY/IdeaProjects/demo/src/main/webapp/WEB-INF/uploadFiles/";
            destinationFileName = RandomStringUtils.randomAlphanumeric(32) + "." + sourceFileNameExtension;
            destinationFile = new File(fileUrl + destinationFileName);]
            ÀúÀåÇÒ Æú´õ °æ·Î + ÀûÀıÇÏ°Ô º¯°æÇÑ ÀÌ¸§À¸·Î ÆÄÀÏ »ı¼º.
```
#### 9.multipartÆÄÀÏÀ» ÀÌÆÄÀÏ¿¡ µ¤¾î¾²±â.
```
destinationFile.getParentFile().mkdirs();
               files.get(i).transferTo(destinationFile);
```
#### 10. post¹æ½ÄÀ¸·Î ³Ñ¾î¿Â º¯¼ö Ã³¸®¿¡ ´ëÇØ.
>parameter¿¡ HttpServletRequest request¸¦ ¼±¾ğÇÏ°í, equest.getParameter("id")°°Àº ½ÄÀ¸·Î ¹Ş¾Æ¿À¸é µÈ´Ù.
¾öÃ» ³ë°¡´Ù ¶Ù´Â°É·Î ¾Ë°í ÀÖ¾ú´Âµ¥, »õ·Î¿î°É ¹è¿ü´Ù.

#### 11. ´ÙÁßÆÄÀÏ ¾÷·Îµå, µ¥ÀÌÅÍº£ÀÌ½º ¿¬°á±îÁö ±¸Çö ÇßÀ¸´Ï, ÀÌÁ¦ CRUD¸¦ ¸¸µé¾î ºÁ¾ß°Ú´Ù. ±×ÈÄ, facebook OAUTH, ÀÌ¸ŞÀÏ ÀÎÁõ±â´É ±îÁö ±¸ÇöÇØº¸ÀÚ.

### ORM(Object Relation Mapping)¿¡ ´ëÇØ
#### °´Ã¼¿Í µ¥ÀÌÅÍº£ÀÌ½º ºÒÀÏÄ¡ ¹®Á¦¸¦ ÇØ°áÇÏ±â À§ÇÑ µµ±¸.
#### MyBatis, JPA. MyBatis¸¦ ¸¹ÀÌ ½èÁö¸¸ JPA¸¦ ¸¹ÀÌ ¾²´Â Ãß¼¼¶ó°í ÇÑ´Ù.
#### ±âÁ¸¿¡´Â MyBatis¸¦ »ç¿ëÇÒ¶§´Â mapperÅ¬·¡½º, ±×¸¦ À§ÇÑ xml, mybatis¼³Á¤À» À§ÇÑ xmlÆÄÀÏ µî ÀıÂ÷°¡ Á¶±İ º¹ÀâÇßÀ¸³ª, JPA¸¦ ¾²´Ï ÀıÂ÷°¡ Á¶±İ ´õ °£´ÜÇØ Á³´Ù.
#### relation°ú MappingÀ» À§ÇÑ class(model), ±×¸¦ ±¸ÇöÇÏ´Â Repositry interface ¸¸ ±¸ÇöÇÏ¸é, JPA¿¡¼­ ±âº»À¸·Î Á¦°øÇÏ´Â ÇÔ¼ö¸¦ ¾µ ¼ö ÀÖ¾î ÆíÇÏ´Ù.
#### ¶ÇÇÑ mybatis¿¡¼­ query mappingÀ» ÇÏ´ø ±â´Éµµ ÃæºĞÈ÷ Áö¿øÀ» ÇÏ´Ï JPA°¡ ÁÁ´Ù°í »ı°¢ µÈ´Ù.

### JPA »ç¿ëÀ» À§ÇÑ ÀıÂ÷.
#### @Entity´Â Å¬·¡½º°¡ µ¥ÀÌÅÍº£ÀÌ½º Å×ÀÌºíÀ» ¸ÅÇÎÇÏ´Â ¿ªÇÒÀ» ÇÑ´Ù.
#### @Repository´Â EntityÁ¶ÀÛ¿¡ ÇÊ¿äÇÑ Äõ¸®¸¦ ¸Ş¼­µåÈ­ ÇØ¼­ »ç¿ëÇÒ ¼ö ÀÖ´Â ¿ªÇÒÀ» ÇÑ´Ù.
#### ¿¬°ü°ü°è
> 1:1, 1:N, N:1, N:N @ManyToOne, @OneToMany
> @ManyToOneÀº Áï½Ã ·ÎµùÀÌ ±âº»°ªÀÌ´Ù. Áï½Ã ·ÎµùÀ¸·Î ½ÇÇàµÉ ¶§´Â ¿¬°áµÈ ¿£Æ¼Æ¼ Á¤º¸±îÁö ÇÑ¹ø¿¡ °¡Á®¿À·Á°í ÇÏ¹Ç·Î ¼º´É¿¡ ¹®Á¦°¡ »ı±æ ¼ö ÀÖ´Ù. Áö¿¬·Îµù µÇµµ·Ï ¼³Á¤ÇÏ´Â°ÍÀÌ ÁÁ´Ù
. @ManyToOne(fetch = FetchType.LAZY)
> @OneToMany¸¦ »ç¿ëÇÒ °æ¿ì mappedBy¸¦ ÅëÇØ ÁÖÀÎÀ» ¸í½ÃÇØÁØ´Ù. @OneToMany(mapperBy = "school")
#### Repository.save(new entity)Çü½ÄÀº insert±¸¹®°ú °°´Ù. ³ª¸ÓÁö´Â update¿Í °°´Ù.
#### @AutoWired -> ÀÇÁ¸¼º ÁÖÀÔ. Repository»ç¿ëÇÒ¶§ »ç¿ëÇÑ´Ù.


#### 1. Relation°ú MappingÀ» À§ÇÑ Model Å¬·¡½º Á¤ÀÇ
> @Entity AnotationÀ» ºÙ¿©Áà¾ß ÇÔ.
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
#### 2. »ç¿ëÀ» À§ÇÑ Repository Å¬·¡½º Á¤ÀÇ.
> @Repository AnnotationÀ» ºÙ¿©Áà¾ß ÇÔ.
```
@Repository
public interface BoardRepository extends JpaRepository<board, Long> {

    board findByusername(@Param("username")String username);
}
```
#### 3. »ç¿ëÇÒ Controller¿¡¼­ Autowierd¼³Á¤ ÈÄ »ç¿ë(ÀÇÁ¸¼º ÁÖÀÔ)
```
@Autowired
  BoardRepository BoardRepository;
```
#### 4. JPA¿¡¼­ Á¦°øÇÏ´Â ±âº»ÀûÀÎ CRUDÇÔ¼ö.
```
¹İÈ¯Å¸ÀÔ findByÇÊµå¸í(Parameter);
board findByusername(@Param("username")String username);
```

#### 5. @Query AnnotationÀ» »ç¿ëÇØ ÇÔ¼ö¸¦ ¸¸µé ¼ö ÀÖ´Ù. ´Ù¸¸ JPQL·Î ÀÛ¼ºÇÏ¿©¾ß ÇÏ¸ç, º°ÄªÀº ÇÊ¼ö·Î »ç¿ëÇÏ¿©¾ßÇÑ´Ù. (ÀÌ ºÎºĞ¶§¹®¿¡ ¿À·¡°É¸²)
```
 SELECT m FROM Member AS m where m.username = 'HY'
 º°ÄªÀ» ÁöÁ¤ÇÏ´Â AS´Â »ı·« °¡´ÉÇÏ´Ù.
 @Query("select u from board u where u.username = :myname")
    List<board> customfunc(@Param("myname") String name);
 ```
 > @Param ÀÌ ÀÛµ¿µÇÁö ¾Ê¾Æ ÇÑÂüÀ» °í»ı ÇÏ¿´´Ù. ¾Ë°íº¸´Ï mybatis¿¡¼­ jpa·Î ¹Ù²Ù´Â Áß¿¡ @ParamÀ» mybatisÆĞÅ°Áö¿¡¼­ ¹Ş¾Æ¿Í¼­ °è¼Ó ¿¡·¯°¡ ³ª´Â °ÍÀÌ¾ú´Ù... ÆĞÅ°Áö¸¦ ¹Ù²ãÁÖ´Ï ¹Ù·Î ÇØ°á µÇ¾ú´Ù.. Á¤¸» Çã¹«ÇÏ´Ù.

 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
 <img width="813" alt="2018-09-30 7 27 03" src="https://user-images.githubusercontent.com/37579650/46257611-bbb57e00-c4f7-11e8-9721-942143f2d2ae.png">
<img width="809" alt="2018-09-30 7 27 11" src="https://user-images.githubusercontent.com/37579650/46257612-bbb57e00-c4f7-11e8-99dd-ea79d445a24a.png">
<img width="807" alt="2018-09-30 7 27 17" src="https://user-images.githubusercontent.com/37579650/46257613-bbb57e00-c4f7-11e8-94c5-a9c4fed5445a.png">

### 6. @Modifying, @Query¸¦ ÀÌ¿ëÇØ Ä®·³ ¼Ó¼ºÀ» ¹Ù²Ù´Â ÇÔ¼ö¸¦ ÀÛ¼ºÇÏ´Ï
```
@Modifying
    @Query("update user_schema s set s.auth=1 where s.id=?1")
    void Authuser(@Param("id")String id);

javax.persistence.TransactionRequiredException: Executing an update/delete query
```

### ¿¡·¯°¡ ¹ß»ıÇÏ¿´´Ù. ¿øÀÎÀ» Ã£Áö ¸øÇÏ°Ú´Ù.
> @Modifying »Ó¸¸¾Æ´Ï¶ó @Transactional ¾î³ëÅ×ÀÌ¼Çµµ Ãß°¡·Î ÀÛ¼ºÇÏ´Ï ÀÛµ¿ÇÏ¿´´Ù.
ÀÌ°Í¶§¹®¿¡ Á¤¸» °í»ıÇÑ°Í °°´Ù. @Transactional ¾î³ëÅ×ÀÌ¼ÇÀÌ ¹«½¼¿ªÇÒÀ» ÇÏ´ÂÁö ¾Ë¾ÆºÁ¾ß °Ú´Ù.
>@TransactionalÀº ÀÌ¸§¿¡¼­ ¾Ë ¼ö ÀÖµíÀÌ Transaction°ú °ü·ÃÀÖ´Â °ÍÀÌ¶ó°í ÇÑ´Ù. DB½Ã°£¿¡ ¹è¿î Æ®·£Àè¼Ç°ú ¶È°°Àº °ÍÀÌ´Ù. ÇÑ ¿¬»êÀÇ ´ÜÀ§, Äõ¸®µéÀÇ ÁıÇÕ... ModifyingÀ» ÇÒ

##JPA
JPA¸¦ »ç¿ëÇÏÁö ¾ÊÀ»¶§ ¹®Á¦.
jdbc¸¦ Á÷Á¢»ç¿ë.
Query°¡ ´ëºÎºĞ ºñ½ÁÇÏÁö¸¸ ´Ù¸¥°Íµµ ¸¹´Ù.
¹İº¹ÀûÀÎ ÄÚµå°¡ ¸¹´Ù.
¿©·¯°¡Áö ¹®Á¦¸¦ ÇØ°áÇÏ±â À§ÇØ ORM»ç¿ë
spring boot¿¡¼­´Â Hikari »ç¿ë

µµ¸ŞÀÎ ¸ğµ¨ ±â¹İ »ç¿ë.
°´Ã¼ÁöÇâÀÇ ÀåÁ¡À» È°¿ëÇÏ±â ÁÁ´Ù.
°¢Á¾ µğÀÚÀÎÆĞÅÏ
ÄÚµå Àç»ç¿ë
ºñÁî´Ï½º ·ÎÁ÷ ±¸Çö ¹× Å×½ºÆ® ÆíÇÔ
ORMÀÌ¶õ ¾ÖÇÃ¸®ÄÉÀÌ¼ÇÀÇ Å¬·¡½º¿Í sqlµ¥ÀÌÅÍº£ÀÌ½ºÀÇ Å×ÀÌºí »çÀÌÀÇ ¸ÊÇÎ Á¤º¸¸¦ ±â¼úÇÑ ¸ŞÅ¸µ¥ÀÌÅÍ¸¦ »ç¿ëÇÏ¿© °´Ã¼¸¦ sqlµ¥ÀÌÅÍº£ÀÌ½ºÀÇ Å×ÀÌºí¿¡ ÀÚµ¿À¸·Î ¿µ¼ÓÈ­ ÇØÁÖ´Â ±â¼ú

hibernate°¡ db¿¡µû¶ó ¾Ë¸Â´Â sql·Î ¹Ù²ãÁØ

Å×ÀÌºí°ú Å×ÀÌºí°£ÀÇ ¿Ü·¡Å°´Â ÇÑ ´Ù¸¥Å×ÀÌºíÀÇ ÁÖÅ°¸¦ ¿Ü·¡Å°¸¦ ¼³Á¤. ´Ù¸¥ µÎ Å×ÀÌºíÀÇ ¿Ü·¡Å°¼³Á¤ ºÒ°¡.

@Entity ÀÌ Å¬·¡½º°¡ µ¥ÀÌÅÍº£ÀÌ½º°¡ ~¶ó´Â Å×ÀÌºí¿¡ ¸ÊÇÎÀÌµÇ´Â Å¬·¡½º´Ù.
@id : ÁÖÅ°¿¡ ¸ÊÇÎ
@GenteratedValue: ÀÚµ¿À¸·Î »ı¼ºµÇ´Â °ªÀ» »ç¿ëÇÏ°Ú´Ù. db¿¡ ÀÌ¹Ì Å×ÀÌºíÀÌ ¸¸µé¾îÁ® ÀÖ°í, ±× °ªÀ» »ç¿ëÇÒ¶§´Â IDENTITY

spring.jpa.hibernate.ddl-auto=update, ¾÷µ¥ÀÌÆ® , create ·Î ÇÏ¸é ¸Å¹ø Áö¿ì°í »õ·Ó°Ô ¸¸µå´Â°ÍÀÌ´Ù.
> Entity class¿¡ ¼Ó¼º Ãß°¡ÇÏ¸é relation¿¡ ÀÚµ¿À¸·Î Ãß°¡µÈ´Ù.

@Entity ¸ÊÇÎ
Annotation ±â¹İ ¼³Á¤
@Entity´Â ÀÚµ¿À¸·Î Å×ÀÌºí·Î ¸ÊÇÎ »ç½Ç»ó @Table AnnotationÀÌ »ı·«µÇ¾î ÀÖÀ½. ±âº»ÀûÀ¸·Î Å¬·¡½º ÀÌ¸§°ú µ¿ÀÏÇÑ ¿£Æ¼Æ¼ »ç¿ë
@Entity(name="sdasad")À¸·Î ¿£Æ¼Æ¼ ¸ÊÇÎ º¯°æ
@Table¿¡¼­ »ç¿ëÇÏ´Â ±âº» °ªÀÌ EntityÀÇ ÀÌ¸§ÀÌ´Ù. ¾Æ¹«·± ¼³Á¤À» ÇÏÁö ¾ÊÀ¸¸é ±âº»ÀûÀ¸·Î Å¬·¡½ºÀÌ¸§°ú °°Àº entity¸ÊÇÎ.


db¿¡¼­ UserÅ°¿öµå°¡ ÀÖ¾î¼­ »ç¿ëÇÒ ¼ö ¾ø´Ù. @Entitiy(name = "fdsafsd") ÀÇ ¸ÊÇÎÀº ¸ÊÇÎµÇ´Â ¸±·¹ÀÌ¼ÇÀÇ Á¤º¸¸¦ ¹Ù²Ù´Â °ÍÀÌ ¾Æ´Ï¶ó, »ç¿ëµÉ Entity Å¬·¡½ºÀÇ ÀÌ¸§À» ¼³Á¤ÇØ ÁÖ´Â°Í. ¿£Æ¼Æ¼ ÀÌ¸§À» ÀÌ¿Í°°Àº ¹æ¹ıÀ» ÅëÇØ ¹Ù²Ü ¼ö ÀÖ´Ù.

@Column(nullable = false, unique = true);

@Temporal ¾î³ëÅ×ÀÌ¼Ç
```
@Temproal(TemporalType.TIMESTAMP)À¸·Î ¼³Á¤ÇÏ¸é ³¯Â¥ ½Ã°£,
@Temproal(TemporalType.TIME) - > ½Ã°£¸¸.

@Transient ¸¦ Ãß°¡ÇÏ¸é columnÀ¸·Î ¸¸µéÁö ¾Ê´Â´Ù
```

@Transient
private String no; ¶ó°í ÇÏ¸é Å×ÀÌºí¿¡ no ¼Ó¼ºÀÌ Ãß°¡µÇÁö ¾Ê´Â´Ù

Class ->  Entity Type
vairable -> Value Type

±âº»ÀûÀ¸·Î db¿¡¼­ Äõ¸®¸¦ ¸¸µå´Â°ÍÀÌ ¾Æ´Ï¶ó JAP·Î EntityÅ¬·¡½º¸¦ ¼±¾ğÇÏ¸é DB¿¡ Å×ÀÌºíÀÌ Çü¼ºµÈ´Ù.

ValueÅ¸ÀÔ ¸ÅÇÎ.
@Embadable ¾î³ëÅ×ÀÌ¼Ç »ç¿ëÇÏ¿© Å¬·¡½º ÇÏ³ª Á¤ÀÇ, ±× Å¬·¡½º¸¦ value·Î °®´Â Å¬·¡½º¿¡¼­

private Adress temp ¶ó°í ¼±¾ğÇÏ¸é Address Å¬·¡½ºÀÇ ¿ä¼Ò°¡ dbÅ×ÀÌºíÀÇ ¼Ó¼ºÀ¸·Î Ãß°¡µÈ´Ù.

```
@Embeded
@AttributePverrodes({
  @AttributePverride(name="street", column=@Column(name="home_street") )
  })
```
  private Address adress·Î ¿À¹ö¶óÀÌµù ÇØ¼­ »ç¿ë °¡´É. AddressÀÇ street ¿ä¼Ò°¡ home_street¶ó´Â ÀÌ¸§À¸·Î µé¾î¿À°Ô µÈ´Ù.

  1´ë´Ù ¸ÊÇÎ @OneToMany
  ¾î¶² ¿£Æ¼Æ¼°¡ ÀÖ°í ´Ù¸¥ ¿£Æ¼Æ¼°¡ ÀÖ´Ù.
  °ü°è´Â Ç×»ó µÎ°¡Áö ¿£Æ¼Æ¼°¡ ¸Â¹°·Á ÀÖ´Ù.

  ¼Ó¼ºÀÌ collectionÀÌ ¾Æ´ÑÂÊÀÌ one

  Owner Å×ÀÌºí¿¡¼­ ¿Ü·¡Å°¸¦ »ı¼ºÇÏ°í °®°íÀÖ°Ô µÈ´Ù. ±× ¿Ü·¡Å°´Â »ó´ë ¿£Æ¼Æ¼ÀÇ id¸¦ ÂüÁ¶ÇÑ´Ù.

  ¾î¶²°ü°èÀÇ ÁÖÀÎ ÀÌ¶ó´Â°Ç °ü°è¸¦ ¼³Á¤ÇßÀ»¶§ ±× °ªÀÌ ¹İ¿µÀÌ µÇ´Â°Í.

@ManyToOneÀº ¿Ü·¡Å°¸¸ Ãß°¡ÇÏ´Â ¹İ¸é
@OneToMany´Â Á¶ÀÎÅ×ÀÌºíÀ» »õ·Î ¸¸µç´Ù. ±× Å×ÀÌºí¿¡ °ü°è¿¡ ´ëÇÑ Á¤º¸°¡ ÀúÀåµÇ¸ç ¿Ü·¡Å°¸¦ µû·Î »ı¼ºÇÏÁö ¾Ê´Â´Ù.

¼­·Î ÂüÁ¶ÇÏ´Â ¾ç¹æÇâ °ü°è¸¦ ¸¸µé ¼öµµ ÀÖ´Ù. ¾çÂÊ¿¡ OneToMany, ManyToOneÀ» ¼±¾ğÇÏ¸é ¾ç¹æÇâ ¸ÊÇÎÀÌ¶ó°í »ı°¢ÇÒ ¼ö ÀÖÁö¸¸ ÀÌ°ÍÀº µÎ°³ÀÇ ´Ü¹æÇâ °ü°èÀÌ´Ù. ¾ç¹æÇâ °ü°è¸¦ ¼³Á¤ÇÏ·Á¸é µû·Î ¼³Á¤À» ÇØÁà¾ßÇÑ´Ù. ¾ç¹æÇâ °ü°è¸¦ ¼³Á¤ÇÏ·Á¸é
@OneToMany(mappedBy = "owner")¸¦ Á¤ÀÇ ÇØ¾ßÇÏ¸ç mappedBy ´Â OneToManyÂÊ¿¡ Á¤ÀÇ.
ÀÌ¶§ °ü°è¸¦ ¼³Á¤½Ã¿¡ ¾çÂÊ¿¡ µÑ´Ù °ü°è¸¦ ¼³Á¤ÇØ ÁÖ¾î¾ß ÇÑ´Ù. @OneToManyÀÎ ÂÊ¿¡ .add.. ¸¦ ÇØÁÖ°í @ManyToOne¿¡ setOwner¼³Á¤À» ¾çÂÊÀ¸·Î ¼³Á¤ÇØÁÖ¾î¾ß Á¤»óÀûÀ¸·Î °ü°è Çü¼ºÀÌµÊ. ¾ç¹æÇâ °ü°èÀÎµ¥ ÇÑÂÊ¿¡¸¸ addÈ¤Àº set ÇØÁØ´Ù´Â°Ç ¸ÂÁö¾Ê´Â°Í. add´Â ÇÊ¼öÀûÀ¸·Î ¼öÇàÇØ¾ßÇÏ´Â ÄÚµå´Â ¾Æ´Ï´Ù. ÇÏÁö¸¸ °´Ã¼ÁöÇâÀûÀ¸·Î »ı°¢ÇßÀ»¶§ µÑ´Ù ÇÏ´Â°ÍÀÌ ÁÁ´Ù.

ÀÌ»óÀûÀÎ °ÍÀº Convenient method¸¦ ¸¸µé¾î »ç¿ëÇÏ´Â °Í.
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

EntityÀÇ »óÅÂ Cascade Option.
@OneToMany, @ManyToOne¿¡ Cascade ¿É¼ÇÀÌ ÀÖ´Ù.
cascade¶õ entityÀÇ »óÅÂº¯È­¸¦ ÀüÀÌ½ÃÅ°´Â °Í.
»óÅÂ´Â Å©°Ô 4°¡Áö°¡ ÀÖ´Ù. Transient Removed Persistant Detached
Transient : °´Ã¼°¡ db¿¡ ÀúÀåµÉÁö ¾ÈµÉÁö jpa, hibernate°¡ ÀüÇô ¸ğ¸£´Â »óÅÂ. saveÇÏ±â Àü.
SAVE¸¦ ÇÏ¸é persistent»óÅÂ°¡ µÈ´Ù. save¸¦ ÇÑ´Ù°í °´Ã¼°¡ ¹Ù·Î µé¾î°¡´Â °ÍÀº ¾Æ´Ï´Ù. ÀÌ »óÅÂ·Î °ü¸®ÇÏ°í ÀÖ´Ù°¡ ÀÌÂë µÆÀ¸¸é db¿¡ ³Ö¾î¾ß °Ú´Ù. ÆÇ´ÜÇÏ´Â ±× ½ÃÁ¡¿¡ ÀúÀåÇÏ°Ô µÈ´Ù. save¸¦ È£ÃâÇß´Ù°í ÇØ¼­ ±× Áï½Ã insert Äõ¸®°¡ ¹ß»ıÇÏ´Â °ÍÀº ¾Æ´Ï´Ù. save¸¦ È£ÃâÇÏ¸é hibernate°¡ ¾Æ´Â »óÅÂ persistant 1Â÷Ä³½¬. ÀÎ½ºÅÏ½º°¡ cache°¡ µÈ »óÅÂ. ÀÌ»óÅÂ¿¡¼­ ´Ù½ÃÇÑ¹ø ÀÌ ÀÎ½ºÅÏ½º¸¦ ´Ş¶ó°í ÇÏ¸é ¼¿·ºÆ® Äõ¸®°¡ ¹ß»ıÇÏÁö ¾Ê´Â´Ù. cacheÇÏ°í ÀÖ´Â°É ÁÙ°Ô ÇÏ¸ç ÁØ´Ù. db¿¡¼­ ³ª¿À´Â°ÍÀÌ ¾Æ´Ô. ÀúÀåÀ» ÇÏÁöµµ ¾ÊÀº »óÅÂ¿¡¼­ ÁÖ´Â°Í. transactionÀÌ ³¡³ª´Â Áï commitÀÌ ÀÏ¾î³ª¸é, insertÄõ¸®°¡ ¹ß»ıÇÑ´Ù. -> Áß°£¿¡ °ªÀ» ¹Ù²Ù´Âµî ºÒÇÊ¿äÇÑ ¾×¼ÇÀ» ÃëÇÏÁö ¾Ê´Â ÀåÁ¡. °´Ã¼¸¦ °è¼Ó °¨½ÃÇÏ°í ÀÖ´Ù°¡ Æ®·£Àè¼ÇÀÌ ³¡³ª¸é Äõ¸® ¼öÇà. ( Dirty checking ÀÌ °´Ã¼ÀÇ º¯°æ»çÇ×À» °è¼Ó °¨ÁöÇÑ´Ù.)

removed»óÅÂ¿¡ ¸Ó¹°·¯ ÀÖ´Ù°¡ commitÀÌ ÀÏ¾î³¯¶§ »èÁ¦ÇÑ´Ù.

 hibernate°¡ persistant »óÅÂ·Î °ü¸®ÇÏ°í ÀÖ´Ù.
@OneToMany(cascade =  )

¿¹¸¦µé¾î °Ô½Ã±Û°ú ´ñ±ÛÀÇ °ü°è. °Ô½Ã±ÛÀÌ »èÁ¦µÇ¸é ´ñ±Ûµµ »èÁ¦µÇ¾î¾ß ÇÑ´Ù.
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

@OneToMany(cascade =CascadeType.PERSIST)·Î ¼³Á¤À» ÇÏ¸é. post.save()·Î ÀúÀåÀ» ÇÒ¶§ ÀÌ persistant¸¦ ¾Ë·ÁÁÖ¼¼¿ä. transient¿¡¼­ ³Ñ¾î°¥¶§ °°ÀÌ persistant°¡µÇ°í ÀúÀåÀÌ µÈ´Ù. CascadeType.REMOVE ¼³Á¤Àº Áö¿ï¶§ Æ÷½ºÆ®¸¦ »èÁ¦ÇÏ´Â¼ø°£ removed»óÅÂ°¡ ÀüÆÄ°¡ µÇ°í commentµµ removed»óÅÂ°¡ µÅ¼­ °°ÀÌ Áö¿öÁØ´Ù. ±×³É CASCADETYE.ALL·Î ÀüºÎ ÀüÆÄÇÏµµ·Ï ¼³Á¤ÇÏ¸é ÆíÇÏ´Ù.
```

Fetch ¿¬°ü°ü°èÀÇ ¿£Æ¼Æ¼¸¦ ¾î¶»°Ô °¡Á®¿Ã°ÍÀÎ°¡. Áö(Eager?) ³ªÁß¿¡(Lazy?) .

OneToMany´Â ±âº»ÀûÀ¸·Î Lazy ¸¹À¸´Ï±î.
ManyToOneÀº ±âº»ÀûÀ¸·Î Eager. »ı°¢ÇØº¸¸é ÇÕ¸®ÀûÀÌ´Ù.

ÀÌ default¼³Á¤ lazy·Î ÀÎÇØ, ¿¹¸¦µé¾î post¿¡ ÀûÇôÀÖ´Â comment·Î °¡Á®¿Ã¶§ n+1¼¿·ºÆ® ¿¡·¯°¡ »ı±æ¼ö ÀÖ´Ù. ÀÌ·± fetchÀü·«À» Àß Á¤ÇÏ´Â°Ô ¼º´É¿¡ Å« ¿µÇâÀ» ¹ÌÄ§.

½ºÇÁ¸µ µ¥ÀÌÅÍ JPA.
data access object ¿ªÇÒÀ» ÇÏ´Â repository¸¦ Á¤ÀÇ.

```
@Repository
@Transactional
public class PostRepository{

  @AutoWired º¸´Ù
  @PersisenceContext¸¦ ¾²´Â°Ô ÁÁ´Ù.
  ½ºÇÁ¸µ ÄÚµå¸¦ ÃÖ´ëÇÑ °¨Ãß´Â°Ô JPAÀÇ ¿øÄ¢ÀÌ¶ó..
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
ÀÌ·¸°Ô Àß ¾²Áö ¾Ê´Â´Ù.
```

ÈÎ¾À Æí¸®ÇÑ ¹æ¹ı. ÃÖ±Ù¿¡ °¡Àå Áøº¸µÈ ÇüÅÂ

```
@Repository
public interface PostRepository extends JpaRepository<Post, Long>{


}
```

¿ø·¡´Â @EnableJpaRepositories¸¦ ºÙ¿©¾ß ÇÏ´Âµ¥ @SpringBootApplicationÀÌ ÀÚµ¿À¸·Î ¼³Á¤ ÇØ ÁØ´Ù.

Äõ¸®¸¦ ¶ç¿üÀ»¶§ ?·Î ³ªÅ¸³ª´Â °ªÀ» º¸´Â ¹æ¹ı. Äõ¸® È®ÀÎ¾ÈÇÏ°í ÇÒ°Å¸é hibernate¸¦ ¾²Áö¸¶¶ó. ¼º´É¿¡ ¹®Á¦°¡ »ı±æ ¼ö ÀÖ´Ù.
```
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=TransactionRequiredException
loggin.level.org.hibernate.type.descriptor.sql=trace
```

SpringData Common
»ó¼Ó¹Ş¾Æ¼­ Interface¸¦ ¸¸µç JpaRepository´Â Repository(±â´É x), CrudRepository, PagingAndSortingRepository //½ºÇÁ¸µµ¥ÀÌÅÍ Common// ¿¡¼­ ±â´ÉÀ» ´õ Ãß°¡ÇÑ°Í.

ÀÌ·¯ÇÑ °ÍµéÀº @NoRepositoryBean AnnotationÀÌ ºÙ¾îÀÖ¾î ºóÀ» ¸¸µé¾î¼­ µî·ÏÇÏ´Â°ÍÀ» ¹æÁöÇÑ´Ù. (ÀÌ°ÍÀ» »ó¼Ó¹Ş¾Æ »ç¿ëÇÏ¶ó´Â °Í. Áß°£´Ü°è Repository, ½ÇÁ¦ Repository°¡ ¾Æ´ÔÀ» ÀÇ¹Ì)

CrudRepository : Save, SaveAll, findById, existsById(Á¸ÀçÀ¯¹« ÆÇ´Ü), findAll, findAllById

@TestÀÇ °æ¿ì´Â ¾îÂ÷ÇÇ ¸ğµÎ rollbackÀÌ±â ¶§¹®¿¡ hibernate°¡ ½ÇÁ¦·Î Äõ¸®¸¦ ³¯¸®Áö ¾Ê´Â´Ù.

PagingAndSortingRepository : findAll(Pageable page)
postRepository.findAll(PageRequest.of(0,10)) new PageRequest ¿¡¼­ PageRequest.of·Î ¹Ù²ñ. deprecated°¡ ¹ß»ıÇÑ´Ù.

nullÃ³¸®
OptionalÀº nullÀÌ ¾ø´Ù. isEmpty»ç¿ë.

Query¸¸µé±â
±âº»ÀûÀÎ naming ±ÔÄ¢À¸·Î ÇÔ¼ö»ç¿ë, Á÷Á¢ ¸¸µé°íÀÚ ÇÒ¶§´Â @Query Annotation »ç¿ë. ±ÔÄ¢ Âü°í.

Like¿Í ºñ½ÁÇÑ ±â´ÉÀ» ÇÏ´Â Containµµ ÀÖ´Ù.
findByCommentContains¿Í °°ÀÌ »ç¿ë °¡´É -> ÀÌ¿Í°°ÀÌ »ç¿ëÇÏ¸é Like Query°¡ ¹ß»ıÇÑ´Ù.

Async ¾î³ëÅ×ÀÌ¼ÇÀ» »ç¿ëÇÏ¸é ºñµ¿±â·Î Ã³¸®°¡´É.¼º´ÉÀ» ÃÖÀûÈ­ ÇÏ·Á¸é ºñµ¿±â Ã³¸®º¸´Ù, Äõ¸®¸¦ ÃÖÀûÈ­ ÇÏ´Â°ÍÀÌ ¼º´É°³¼±¿¡ ´õ ÁÁ´Ù.
ºñµ¿±â Äõ¸®´Â °¡±ŞÀû ¾È¾²´Â°ÍÀÌ ÁÁÀ½

Custom Repository 
Á¢¹Ì»ç·Î Impl ºÙÀÌ´Â °ÍÀÌ º¸ÆíÀû.
Ä¿½ºÅÒ 'ÀÎÅÍÆäÀÌ½º'¸¦ ¸¸µé°í, ±×µÚ¿¡ ImplÀÌ¶ó´Â Á¢¹Ì»ç¸¦ ºÙÀÎ '±¸ÇöÃ¼'¸¦ ±¸ÇöÇÑ´Ù. Impl·Î ¼³Á¤µÇ¾î ÀÖ±â ¶§¹®¿¡ ¹«Á¶°Ç ImplÀ» ½á¾ßÇÔ

Insert µÚ¿¡ Select Delete°¡ ÀÖ´Â °æ¿ì, Select°¡ ¾øÀ¸¸é Äõ¸®°¡ ¹ß»ıÇÏÁö ¾ÊÁö¸¸ Select°¡ ÀÖ´Â°æ¿ì Insert°¡ Select¿¡ ¿µÇâÀ» ÁÙ ¼ö ÀÖÀ¸¹Ç·Î InsertÄõ¸®°¡ ¹ß»ıÇÔ.

µ¥ÀÌÅÍº£ÀÌ½º¿¡ delete ½ÌÅ© ¾ÈÇÏ´Â ÀÌÀ¯ : ¾îÂ÷ÇÇ ·Ñ¹é ¿¬»êÀÌ±â ¶§¹®¿¡ delete Äõ¸® ¹ß»ıÇÏÁö ¾ÊÀ½.
