#### Web Sockets
![image](https://user-images.githubusercontent.com/105087933/179432374-04183aa5-d7ac-4d8c-b38f-4113962126e9.png)

#### 🗼서버와 클라이언트 통신 ( HTTP와 AJAX 차이 )
- HTTP는 클라이언트쪽(웹브라우저)에서 Request를 보내고 Server쪽에서 Response를 받으면 이어졌던 연결이 끊기게 되어있다. 그래서 화면의 내용을 갱신하기 위해서는 다시 Request를 하고 Response를 하면서 페이지 전체를 갱신하게 된다.
- AJAX는 html 페이지 전체가 아닌 일부분만 갱신할수 있도록 XMLHttpRequest객체를 통해 서버에 request 한다. XMLHttpRequest는 서버와의 연결을 잡아둔다. Json이나 xml형태로 필요한 데이터만 주고 받으며 DOM을 갱신하기 때문에 그만큼의 자원과 시간을 아낄 수 있다.

 ##### *HTTP 프로토콜* : 클라이언트가 서버에 요청을 보내면 서버는 그에 대한 응답을 보내는 클라이언트 서버 구조로 이루어져 있다.
  ##### ⇒ 요청시 브라우저 url에서 직접 요청 가능하나, 새로고침 되는 단점이 있다.  
       클라이언트 — 메세지 —> 서버를 요청(request)이라 하고,  
       서버 — 메세지 —> 클라이언트를 응답(response)라고 한다.                               
  ###### ☑️ 요청의 종류
        • GET : 자료를 요청할 때 사용
        • POST : 자료의 생성을 요청할 때 사용
        • PUT : 자료의 수정을 요청할 때 사용
        • DELETE : 자료의 삭제를 요청할 때 사용  
  ###### 무상태 프로토콜(Stateless)  
        http는 한번의 request와 response로 이루어져 있고 Back-End는 이 한번의 과정이 끝나면 User를 잊어버린다.  
        HTTP -> 서버가 클라이언트의 상태를 보존하지 않는 무상태 프로토콜이다. 서버가 클라이언트 상태를 보존하지 않는다.  
  
  *※(http 통신 참고) https://inpa.tistory.com/108*  
  
  ##### *AJAX*: 서버에 데이터 요청 시 새로고침 없이 데이터 주고받을 수 있게 하는 브라우저 기능이다.
  ##### ⇒ 새로운 웹페이지로 이동하는 것이 아닌, 동일한 웹페이지 내에서 DOM을 변경하게 된다.
  
  **Ajax는 클라이언트에서 서버로밖에 요청을 못하는 단방향 통신
  WebSocket은 어느 쪽에서든 요청을 보낼 수 있는 양방향 통신**
  
   #### *WebSocket* : 웹 서버와 웹 브라우저가 지속적으로 연결된 TCP 라인을 통해 실시간으로 데이터를 주고 받을 수 있도록 하는 HTML5의 새로운 사양이다.  
  ##### WebSocket을 이용하면 일반적인 TCP소켓과 같이 연결지향 양방향 전이중 통신이 가능하다.서버에게 처음 request를 보내어 연결하는 요청을 하고 서버는 Accept하게 되면 연결이 성립(establish)된다고 한다.
  ##### 연결된 상태에서는 양방향 통신(br-directional)이기 때문에 서버는 유저가 누구인지 알고 있고 먼저 통신을 보낼 수도 있게 된다.  
  ##### → 클라이언트와 서버가 연결되어 있기 때문에 실시간 통신이 가능(Real Time-Networking)하다.   
 
    Real-time web application구현을 위해 널리 사용되어지고 있다.  
    보통 채팅이나 LoL같은 멀티플레이어 게임, 구글 Doc, 증권 거래, 실시간 주식 차트와 같은 실시간이 요구되는 응용프로그램의 개발을 한층 효과적으로 구현할 수 있다.
   