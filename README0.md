[1]. 웹 프로그래밍의 기초

1. Web개발의 이해 - FE/BE
2) 웹의 동작(http에 대해)
HTTP란.
서버와 클라이언트가 인터네상에서 데이터를 주고받기 위한 프로토콜
>장점 . 클라이언트와 서버가 계속 연결된 상태가 아니다. 요청이 있을때만 연결-> 응답을 받으면 연결을 끊어버림 -> 불특정 다수를 대상으로 하는 서비스에 적합하다.
>단점 . 연결을 끊어버리기 때문에 클라이언트의 이전 상황을 알 수 없다(무상태) -> 이때문에 정보를 유지하기 위해서 Cookie 등장.

HTTP (HyperText Transper Protocol)
1. GET : 정보를 요청.
   POST : 정보를 밀어 넣음.
   PUT : 정보를 업데이트 하기위해
   DELETE : 정보를 삭제하기 위해
   등...
2. 요청 URI : 요청하는 자원의 위치를 명시.
3. https는 http에 비해 보안요소가 강화된 것인듯 하다.

4)browser의 동작.
서버에서는 HTML, CSS, JS를 넘겨주고 브라우저에서 엔진을 통해 해석되어 화면에 표시된다. 크롬이 빠른 이유는 구글이 개발한 엔진의 성능 덕분.

6)웹 서버, WAS(Web Application Server)

2. HTML
2)HTML layout 태그.
header, nav, section, footer, aside 등..
