### Axios
***

  #### Axios

  **Axios**는 HTTP 비동기 통신 라이브러리로써, 비동기 방식으로 HTTP 데이터 요청을 실행한다. 내부적으로 AXIOS는 직접적으로 XMLHttpRequest 를 다루지 않고 “AJAX 호출”을 할 수 있다.  
    (참고) https://axios-http.com/kr/docs/intro  
    
  #### *특징*
      - 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 http api 사용
      - Promise(ES6) API 사용
      - 요청과 응답 데이터의 변형
      - HTTP 요청 취소
      - HTTP 요청과 응답을 JSON 형태로 자동 변경
***
  ##### Axios 사용법
    1. 설치
    - yarn 사용하기
  ```
  yarn add axios
  ```  
  
  2. Axios 문법 구성
  ```
  axios({
  url: 'https://test/api/cafe/list/today', // 통신할 웹문서
  method: 'get', // 통신할 방식
  data: { // 인자로 보낼 데이터
    foo: 'diary'
  }
  });
  ```
  
  3. 주로 사용하는 axios 요청(request) 파라미터 옵션
      - method : 요청방식. (get이 디폴트)
      - url : 서버 주소
      - headers : 요청 헤더
      - data : 요청 방식이 'PUT', 'POST', 'PATCH' 해당하는 경우 body에 보내는 데이터
      - params : URL 파라미터 ( ?key=value 로 요청하는 url get방식을 객체로 표현한 것)
      - withCredentials : cross-site access-control 요청을 허용 유무. 이를 true로 하면 cross-origin으로 쿠키값을 전달 할 수 있다.  
    ```
    /* axios 파라미터 문법 예시 */

    axios({
        method: "get", // 통신 방식
        url: "www.naver.com", // 서버
        headers: {'X-Requested-With': 'XMLHttpRequest'} // 요청 헤더 설정
        params: { api_key: "1234", langualge: "en" }, // ?파라미터를 전달
        responseType: 'json', // default

        maxContentLength: 2000, // http 응답 내용의 max 사이즈
        validateStatus: function (status) {
          return status >= 200 && status < 300; // default
        }, // HTTP응답 상태 코드에 대해 promise의 반환 값이 resolve 또는 reject 할지 지정
        proxy: {
          host: '127.0.0.1',
          port: 9000,
          auth: {
            username: 'mikeymike',
            password: 'rapunz3l'
          }
        }, // proxy서버의 hostname과 port를 정의
        maxRedirects: 5, // node.js에서 사용되는 리다이렉트 최대치를 지정
        httpsAgent: new https.Agent({ keepAlive: true }), // node.js에서 https를 요청을 할때 사용자 정의 agent를 정의
    })
    .then(function (response) {
        // response Action
    });
    ```  
    
    4. axios 응답(response) 데이터  
   - axios를 통해 요청을 서버에게 보내면, 서버에서 처리를하고 다시 데이터를 클라이언트에 응답 하게 된다. 이를 .then으로 함수인자로(response)로 받아 객체에 담진 데이터가 바로 응답 데이터이다. 
   ```
       axios({
        method: "get", // 통신 방식
        url: "www.naver.com", // 서버
    })
    .then(function(response) {
      console.log(response.data)
      console.log(response.status)
      console.log(response.statusText)
      console.log(response.headers)
      console.log(response.config)
    })
    {
      data: {}, // 서버가 제공한 응답(데이터)

      status: 200, // `status`는 서버 응답의 HTTP 상태 코드

      statusText: 'OK',  // `statusText`는 서버 응답으로 부터의 HTTP 상태 메시지

      headers: {},  // `headers` 서버가 응답 한 헤더는 모든 헤더 이름이 소문자로 제공

      config: {}, // `config`는 요청에 대해 `axios`에 설정된 구성(config)

      request: {}
      // `request`는 응답을 생성한 요청
      // 브라우저: XMLHttpRequest 인스턴스
      // Node.js: ClientRequest 인스턴스(리디렉션)
    }
   ```  
   
   5. Axios 단축 메소드  
   - GET : axios.get(url[, config])  
   - POST : axios.post(url, data[, config])  
   - PUT : axios.put(url, data[, config])  
   - DELETE : axios.delete(url[, config])  
      ```  
      axios.request(config)

      axios.get(url[, config])

      axios.delete(url[, config])

      axios.head(url[, config])

      axios.options(url[, config])

      axios.post(url[, data[, config]])

      axios.put(url[, data[, config]])

      axios.patch(url[, data[, config]])
      ```  
      
      (참고) https://velog.io/@zofqofhtltm8015/Axios-%EC%82%AC%EC%9A%A9%EB%B2%95-%EC%84%9C%EB%B2%84-%ED%86%B5%EC%8B%A0-%ED%95%B4%EB%B3%B4%EA%B8%B0
***

  <<5주차 회고록>>
    5주차를 회고하려고 보니 3,4주차와 이어서 정말 힘들다. 3주차-4주차는 개념 정리 -> 새로운 지식 습득 -> 구글링 하면서 개념정리(노션에 기록)
    하면 할수록 모르는 것 투성이고, 나름 정리했다고 했는데 빈틈이 꽤 많았다. 리덕스는 어느정도 개념이 잡혔다고 생각했는데... 과제 구현을 못했다.
    심화주차 과제구현을 제대로 하지 못해 무거운 마음으로 미니프로젝트를 시작한다.
    그래도 날 많이 도와줬던 FE 팀원과 같은 조가 되서 마음이 한결 편안해졌지만, 미안한 마음이 크다.
    목요일은 프로젝트 기획하고(그래도 S.A에 대한 피드백이 좋은편이였다), Figma를 처음 써봤다.
    그리고 Figma를 통해 작업한 와이어프레임을 바탕으로 오늘까지 CSS를 통해 뷰를 구현했다.
    정말 CSS 버튼, 블럭, 등ㅇ등... 너무 내 마음대로 되는게 없어서 힘들었다... 여전히 힘들다....
    
    *이제 내가 실행 해야할 것*
 - [ ] 기능구현 (리덕스)
 - [ ] BE와 서버 통신 체크
 
