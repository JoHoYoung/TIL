#### HTTP란
HyperText Transfer Protocol의 약자로 하이퍼텍스트 문서를 교환하기 위하여 사용된 통신 규약이다. 즉, 웹 서버와 클라이언트 간의 통신을 하기 위한 통신 규약입니다

2. HTTP는 연결 상태를 유지하지 않는 프로토콜입니다.

   처음 연결인 Web-Browser로 통해 Web-Client의 요청으로 Web-Server의 서버와 접속하여
   Web-Client의 요청에 대한 응답인 데이터를 전송 후 연결을 종료합니다.
   이러한 심플한 상태이기 때문에 전산 자원이 적게 든다는 장점이 있습니다.
   단점은 연결이 지속적이지 않기에 Web-Client와 연결 종료 후
   추가적인  Web-Client의 요청시 어떤 Web-Client이 요청인지 모른다는 점이 있습니다.
   즉 다수의 Web-Client이 요청시 각각의 Web-Client 요청을 구분 할 수 없어서 
   제대로 된 응답인 데이터를 전송 할 수 없다는 단점이 발생합니다.
   이런 단점을 해소하기 위한 방법은 다음과 같습니다.

INNER(내부) JOIN 과 대비하여 OUTER(외부) JOIN이라고 불리며, JOIN 조건에서 동일한 값이 없는 행도 반환할 때 사용합니다.
즉 A, B 테이블을 JOIN 할 경우, 조건에 맞지 않는 데이터도 표시하고 싶을 때 OUTER JOIN을 사용합니다.

ALTER TABLE PLAYER
RENAME COLUMN PLAYER_ID TO TEAM_ID;

ALTER TABLE TEAM_TEMP
MODIFY (ORIG_YYYY VARCHAR2(8) DEFAULT '20020129' NOT NULL);
alter table ARTICLE change id1 id varchar(50)



##URI와 URL의 차이
URI는 Uniform Resource Identifier 이고,
URL은 Uniform Resource Locator 이다.

URL : www.naver.com/posts
URI : www.naver.com/posts?page=1

요약하자면 URL 은 다음과 같다.
http://test.com/work/sample.pdf
test.com 서버에서 work 폴더안의 sample.pdf 를 요청하는 URL.

URI(통합 자원 식별자) 의 예는 다음과 같다.
1) rewrite 기술을 사용하여 만든 의미있는 식별자
http://test.com/company/location

post/delete/1
위 URI로 접속하면 1번 포스트가 삭제된다. 이러한 URI 설정은 REST를 제대로 적용하지 않은 URI이다.
RESTful한 URI는 정보의 자원만을 나타내야하며 어떤 행위가 포함되지 않도록 해야한다.

URI 를 통해 자원을 명시하고, HTTP method로 어떤작업을 처리할지 적용하는것

위와 같은 URI는 1번 글 자원을 명확히 나타내는 URI이다. 이 자원에 대해 행할 행위는 URI에 포함시키는 것이 아닌 HTTP Method 를 통해 수행하게 된다.

METHOD	역할
POST	POST를 통해 해당 URI를 요청하면 리소스를 생성한다.
GET	GET를 통해 해당 리소스를 조회하고 해당 도큐먼트에 대한 자세한 정보를 가져온다.
PUT	PUT를 통해 해당 리소스를 수정한다.
DELETE	DELETE를 통해 리소스를 삭제한다.

REST란
HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.

데드락이란

프로세스는 운영체제로부터 자원을 할당받는 작업의 단위이고 스레드는 프로세스가 할당받은 자원을 이용하는 실행의 단위입니다.

프로세스는 프로그램 실행시 Code, Data, Stack, Heap의 구조로 되어있는 독립된 메모리 영역을 할당 받습니다.
스레드는 프로세스 내에서 각각 Stack만 따로 할당을 받고 Code, Data, Heap 영역을 공유합니다.

OSI 7계층
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. DataLink
1. Physical

TCP 프로토콜(Transmission Control Protocol)
OSI 계층모델의 관점에서 전송 계층(4계층)에 해당

양종단 호스트 내 프로세스 상호 간에 신뢰적인 연결지향성 서비스를 제공
- IP의 비신뢰적인 최선형 서비스에다가 신뢰적인 연결지향성 서비스를 제공하게 됨
. 신뢰적인 전송을 보장함으로써, 어플리케이션 구현이 한층 쉬워지게 됨
1. 신뢰성 있음 (Reliable)
패킷 손실, 중복, 순서바뀜 등이 없도록 보장
TCP 하위계층인 IP 계층의 신뢰성 없는 서비스에 대해 다방면으로 신뢰성을 제공
2. 연결지향적 (Connection-oriented)                                        ☞ TCP 연결

같은 전송계층의 UDP가 비연결성(connectionless)인 것과는 달리, TCP는 연결지향적 임
이 경우, 느슨한 연결(Loosly Connected)을 갖으므로 강한 연결을 의미하는 
가상회선이라는 표현 보다는 오히려 연결지향적이라고 말함
연결 관리를 위한 연결설정 및 연결해제 필요          ☞ TCP 연결설정, TCP 연결종료
양단간 어플리케이션/프로세스는 TCP가 제공하는 연결성 회선을 통하여 서로 통신

UDP 프로토콜(User Datagram Protocol)
전송 계층의 통신 프로토콜의 하나 (TCP에 대비됨)
- 신뢰성이 낮은 프로토콜로써 완전성을 보증하지 않으나,  
- 가상회선을 굳이 확립할 필요가 없고 유연하며 효율적 응용의 데이타 전송에 사용

1. 비연결성이고, 신뢰성이 없으며, 순서화되지 않은 Datagram 서비스 제공 
- 메세지가 제대로 도착했는지 확인하지 않음 (확인응답 없음)
- 수신된 메세지의 순서를 맞추지 않음 (순서제어 없음) 
- 흐름 제어를 위한 피드백을 제공하지 않음 (흐름제어 없음)
- 검사합을 제외한 특별한 오류 검출 및 제어 없음 (오류제어 거의 없음)
UDP를 사용하는 프로그램 쪽에서 오류제어 기능을 스스로 갖추어야 함
- 데이터그램 지향의 전송계층용 프로토콜 (논리적인 가상회선 연결이 필요없음)
비연결접속상태 하에서 통신 

2. 실시간 응용 및 멀티캐스팅 가능
- 빠른 요청과 응답이 필요한 실시간 응용에 적합
- 여러 다수 지점에 전송 가능 (1:多)
3. 헤더가 단순함
- UDP는 TCP 처럼 16 비트의 포트 번호를 사용하나,
- 헤더는 고정크기의 8 바이트(TCP는 20 바이트) 만 사용
즉, 헤더 처리에 많은 시간과 노력을 요하지 않음


불러오기 , 파싱 , DOM tree , Rendering Tree - > 그리기.

하나의 부모 DOM을 만들어서 이벤트를 처리하는것이 바로 델리게이션이다.

HTML은 기본적으로 트리구조의 DOM을 표현한다.
자식 DOM 요소에 발생한 이벤트는 포괄적으로 보면 부모 DOM에서도 발생한 것으로 인지할 수 있다.

버블링과 캡쳐링은 정 반대로 동작한다.
버블링은 특정 DOM에서 이벤트가 발생하면 하위 DOM으로 부터 부모 DOM으로 한단계씩 전파된다.
캡쳐링은 이벤트가 최상위 부모 DOM부터 하위 DOM까지 전파되는 것을 의미한다.
divs.forEach(function(div) {
	div.addEventListener('click', logEvent, {
		capture: true // default 값은 false입니다.
	});
});

event.stopPropagation();
https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/

화면의 모든 인풋 박스에 일일이 이벤트 리스너를 추가하는 대신 이제는 인풋 박스의 상위 요소인 ul 태그, .itemList에 이벤트 리스너를 달아놓고 하위에서 발생한 클릭 이벤트를 감지합니다. 이 부분이 앞에서 배웠던 이벤트 버블링이죠.

구문분석 단계
먼저, 사용자가 실행한 SQL문이 데이터베이스에서 처음 사용된 문장인지 이미 사용된 문장인지를 공유 풀 영역을 검색하여 확인합니다. 확인하는 이유는 이미 사용된 문장이라면 구문분석(Parsing)이라는 작업을 할 필요가 없고 처음 사용되었다면 정상적으로 구문분석 작업을 해야 하기 때문입니다. 구문분석 단계에서는 SQL문의 문법이 제대로 작성되었는지를 분석하고(예를 들어, SELECT가 SLECC로 잘못 작성되지는 않았는지 등) 사용된 테이블, 뷰 등이 존재하는지를('SELECT * FROM emp'에서 EMP 테이블이 데이터베이스 내에 존재하는지) 확인합니다. SQL문이 실행될 때 가장 빠르게 데이터를 검색해줄 수 있는 방법(Explain Plan)도 찾아줍니다.

실행 단계
구문분석이 정상적으로 실행되면 서버 프로세스는 메모리 영역의 데이터베이스버퍼 캐시영역을 검색하여 해당 테이블이 다른 사용자의 다른 SQL문에 의해 이미 데이터버퍼 캐시영역에 존재하는지를 검색합니다. 만약, 존재하지 않는다면 정의된 테이블의 해당 데이터 파일로부터 테이블을 읽어서 데이터버퍼 캐쉬영역에 저장합니다.

만약, 사용자가 UPDATE, DELETE, INSERT문을 실행하였다면 데이터 버퍼캐쉬 영역에서 새로운 데이터로 변경, 삭제 또는 입력하게 됩니다.

인출단계
실행단계가 끝나면 서버 프로세스는 데이터버퍼 캐쉬영역에서 관련 테이블 데이터를 읽어서 사용자의 클라이언트(P/C) 화면에 보여줍니다.

단, SELECT문을 실행하는 경우에만 인출(Fetch)단계가 실행되고 UPDATE, INSERT, DELETE문 실행 시는 인출단계는 실행되지 않습니다. DML문을 실행하는 경우에 실행 결과가 화면에 출력되는지를 생각해 보세여. 몇 건의 행이 변경, 삭제, 입력되었다는 메시지 만 나타나죠 ? 즉, DML문을 실행할 때는 인출단계는 실행되지 않습니다. SELECT문에 만 적용됩니다.