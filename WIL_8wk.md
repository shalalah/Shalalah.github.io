#### SocketIO vs WebSockets

![Untitled](https://user-images.githubusercontent.com/105087933/180652765-44387aed-aa51-4b12-a814-7be1a222f332.png)
  ⋆ **socket io**는 WebSocket, HTTP long-polling 이라는 두 가지 기술을 통해 통신을 하는 프레임워크다.  
  실시간, 양방향, event 간의 통신을 가능하게 한다. 만약 websocket 이용이 불가능한 경우, socket IO는 다른 방법을 이용해서 계속 작동한다. 
  socket IO는 websocket 뿐 아니라 다른 것도 사용한다. 만약 프록시, 방화벽, 백신 S/W 때문에 연결이 불안정해지고 끊어지면 최대 10초나 기달려하지만 socket IO에서는 안정성과 신뢰성이 높은 프레임워크고 연결이 끊어지면 탄력적으로 다시 연결 시킬 수 있다.  
  *※(socket io 참고) https://socket.io*  
  
![Untitled](https://user-images.githubusercontent.com/105087933/180724059-302b6de9-1c70-4c5a-a836-4b18b9985507.png)
  - 서버 → 클라이언트 ( 서버가 클라이언트에게 메시지 전송 )
    - **socket.emit**  :  서버쪽에서 event를 발생시키는 함수  
    서버에서 이벤트 발생시키면 클라이언트 페이지의 해당 이벤트 리스너에서 처리 
    → 해당 소켓을 통해 클라이언트에게 메시지 전송  
    ```javascript
      socket.emit("event명", msg);
    ```
  - 클라이언트 → 서버 ( 클라이언트가 서버에게 전송한 메시지 수신 )
    - **socket.on**  : 해당 클라이언트에서 메세지를 보냄   
    ```javascript
      // socket.on("event명", 함수/값/변수)
      socket.on("event명", () => {});
    ``` 
  => 👉 socket.emit에 있는 첫번째 argument는 event 즉, text 이다!  → socket.on 뒤에도 같은 string 으로 와야함.  
  
 ##### 🛋 Room : 서로 소통할 수 있는 socket 그룹
  ###### ☑️ room과 관련된 socket.io 코드들
        • socket.join(””) : room에 들어가기 위해 사용  
        • socket.onAny(callback) : 소켓 내에서 발생한 이벤트를 캐치하는 역할을 하는 메서드  
        • socket.id : socket에는 id가 있어서 id로 구별 가능  
        • socket.rooms : socket이 어떤 방에 있는지 알기 위해 사용  
        • socket.to(room) : 방 전체에 메세지를 보낼 수 있음
***  

#### 🚀 webRTC vs Socket.IO : Socket.IO는 서버를 통해 msg를 보냈다면, **webRTC**는 서버로 가지 않고 비디오, 오디오 등을 직접 상대방에게 보낸다(peer to peer 연결).  
![Untitled (1)](https://user-images.githubusercontent.com/105087933/180726072-694b8a01-fd56-4a71-9864-dfdbd9e2f96d.png)  

  - “Signaling” : peer-to-peer로 연결하기 전에 사용자가 어디서 접속하는지 확인해야 할 필요가 있음  
  → 서로의 IP 주소(public인지), 방화벽 열려 있는지, 어떤 포트를 사용할 수 있을지 … 정도를 확인하기 위해 서버가 중개자로 동작하게 되는 것
    이렇게 “Signaling”이 끝나고 서버가 브라우저로 정보를 전송했기 때문에 서로의 위치 파악됨 → peer-to-peer로 직접 연결  

![Untitled (2)](https://user-images.githubusercontent.com/105087933/180727563-29d8c761-753c-4483-8f3a-b1d55c4af840.png)

  **webRTC의 Peer-to-Peer 과정**
  - 누군가 들어왔을 때 알림(webRTC 과정에서 반드시 필요한 부분) → 연결은 “offer”라는 시그널을 대화 상대에게 보내는 것에서 시작하는데, 이 시그널을 직접 만들어 보는 것  
    ⇒ 알림을 받는다는건 이 모든 프로세스를 시작해도 된다는 뜻!(연결의 시작)   
    
  **RTCPeerConnection**
  - 양쪽 브라우저의 연결을 만들기 - 양쪽에서 각각 연결통로를 만들어서 그것들을 서버(socket.IO)사용하여 같이 연결  
    ⇒ 알림을 받는 브라우저가 offer를 만드는 행위를 시작하는 주체라 할 수 있음  
    
  **Signaling process**
  - welcome 이벤트 → Peer A인 브라우저에서 실행됨 → offer를 생성함 → setLocalDescription 가 일어나고 Peer B로 그 offer를 보낸다
  - offer  이벤트 → Peer B인 브라우저에서 실행됨 → server를 통해 offer랑 같이 옴  

  **Answers**
  - Peer A에서 offer를 만들고 setLocalDescription을 함 ⇒ 그걸 서버에 보내고 ⇒ Peer B가 그 offer를 받고(socket on “welcome”) 그 offer로 setRemoteDescription을 함, createAnswer를 하고 ⇒ 그 answer로 setLocalDescription함(getUserMedia & addStream은 Peer B가 방에 들어왔을 때 실행했음) ⇒ answer 이벤트를 발생시켜 서버로 보내서 signaling server(즉, Socket.IO)로 돌아감 ⇒ Peer A에서 setRemoteDescription
  
  **IceCandidate**
  - peer-to-peer 연결의 양쪽에서 IceCandidate라는 이벤트를 실행
    ⇒ iceCandidate(Internet Connectivity Establishment; 인터넷 연결 생성) : webRTC에 필요한 프로토콜들이며, 멀리 떨어진 장치와 소통할 수 있게 하기 위함 → 브라우저가 서로 소통할 수 있게 해주는 방법 → 어떤 소통 방법이 가장 좋을 것인지를 제안할 때 쓰임

  **(추가)Senders**
  - sender는 우리의 peer로 보내진 media stream track을 컨트롤하는 방법  
  
  **(추가)STUN**
  - STUN 서버는 컴퓨터가 공용 IP주소를 찾게 해준다
  - 핸드폰과 컴퓨터가 같은 와이파이를 사용해야 서로 화면에 나타남 → 다른 와이파이를 사용하더라도 공용 IP를 알려주는 것이 필요함 → 공용주소를 알아내서 다른 네트워크에 있더라도 서로 화면에 나타날 수 있도록 STUN서버를 사용하고 있는 것임

**⚠️ webRTC 단점 몇가지**
- 그물망 방식이기 때문에 peer들이 많을 때는 느려진다 → SFU같은 것이 대안이 될 수 있다
