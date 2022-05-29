### DOM (The Document Object Model)

#### DOM이란?
- DOM은 웹 페이지에 대한 인터페이스로, 문서 내의 모든 요소를 정의하고 다양한 프로그램들이 페이지의 컨텐츠, 구조 및 스타일을 읽고 조작할 수 있도록 API를 제공하는 일종의 객체 모델이다.
- 텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하려면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 한다. 
**브라우저의 렌더링 엔진은 웹 문서를 로드한 후, 파싱하여 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재**하는데 이를 DOM이라 한다.
- ** DOM과 랜더링의 관계 ** : 개발자가 HTML 문서를 작성하여 웹 브라우저에게 전송하면 웹 브라우저는 해당 HTML 문서를 Tree 형태의 데이터를 생성하는데 이 데이터를 DOM이라고 한다.  
웹 브라우저는 DOM을 바탕으로 화면을 구성하여 사용자에게 보여준다.
![image](https://user-images.githubusercontent.com/105087933/170873572-714472ee-48cb-4739-a4fc-94e22aed2104.png)

  ##### (참고)JavaScript vs DOM
    JavaScript는 브라우저가 읽고 어떤 작업을 수행할 수 있는 언어이고, DOM은 이 작업이 이루어지는 장소를 말한다.
    사실 우리가 'JS로 하는 것'이라고 생각하는 것은 정확히는 'DOM API'다.  
    DOM은 브라우저에 의해 기록되는 모든 것이고, JS는 이를 조작할 수 있는 언어일 뿐이다.
    따라서 JS는 브라우저 밖의 DOM API가 없는 환경에서도 동작할 수 있다. (ex. Node.js 등)


#### \*웹 페이지 빌드 과정에서의 DOM의 쓰임새
- 웹 브라우저가 원본 HTML 문서를 읽어들인 후, 스타일을 입히고 대화형 페이지로 만들어 뷰 포트에 표시하기까지의 과정을 Critical Rendering Path라고 한다.  
이 과정은 여러 단계로 나누어져 있지만, 이 단계들을 대략 두 단계로 나눌 수 있다.
  - 1단계. 브라우저는 읽어들인 문서를 파싱(원하는 데이터를 분석하여 추출)하여 최종적으로 어떤 내용을 페이지에 렌더링할지 결정한다.  
첫 번째 과정을 거치면 “렌더 트리”가 생성된다. 브라우저는 렌더 트리를 생성하기 위해 다음과 같이 두 모델이 필요하다.
    - DOM(Document Object Model) – HTML 요소들의 구조화된 표현  
    - CSSOM(Cascading Style Sheets Object Model) – 요소들과 연관된 스타일 정보의 구조화된 표현
  - 2단계. 브라우저는 해당 렌더링을 수행한다.

  #### \*브라우저의 Workflow
    ![image](https://user-images.githubusercontent.com/105087933/170872977-8d4b4546-1ce8-4625-8176-3d216c9713f4.png)
- **DOM Tree 생성** : 브라우저가 HTML을 전달받으면, 브라우저의 렌더 엔진이 이를 파싱하고 DOM 노드(Node)로 이뤄진 트리를 만든다. 각 노드는 각 HTML 엘리먼트들과 연관되어있다.
- **Render Tree 생성** : 외부 CSS 파일과 각 엘리먼트의 inline 스타일을 파싱한다. 스타일 정보를 사용하여 DOM 트리에 따라 새로운 트리, 렌더트리를 만든다.

***

### \*서버리스(Serverless)
- 백엔드인데 직접 서버를 관리하지 않는 경우를 뜻한다.서버리스를 활용하면 백엔드를 서버에 올리는 게 아닌,  
백엔드를 작은 함수단으로 쪼개서 내가 직접 관리하지 않는 서버로 올린다(ex. AWS lambda)
- 서버리스가 아닌 경우, 서버는 언제나 요청에 응답할 수 있게 24시간 돌아가고 있지만 서버리스 경우, 내가 업로드한 함수는 잠들어 있다가 리퀘스트가 오면 깨어난다.  
요청한 작업을 수행 후 다시 잠드는데 이 말은 서버가 24시간 깨어있지 않아도 된다는 말이다.

#### \*작동방식
서버를 사용해야 하는 경우, 그러니까 표준 IaaS(Infrastructure as a Service)모델에서 사용자는 용량 단위를 미리 구매한다.  
이는 애플리케이션을 실행하기 위해 ‘상시 가용할 수 있는’ 서버 구성 요소에 대한 비용을 지불하는 것이다. 서버리스의 모델들은 이와 다르다.  
이벤트를 실행할 애플리케이션 코드를 트리거(특정한 작용에 대응하여 자동으로 반작용이 실행되게끔 만드는 논리적 장치)하면 클라우드 제공업체는 
해당 코드에 리소스(서버 자원)를 동적으로 할당하고, 사용자는 코드 실행이 끝나면 비용을 지불하지 않는다.

#### \*서버리스의 두 가지 서비스 형태
- 완전한 서버리스 애플리케이션(혹은 서비스)를 구축하거나, 일부는 서버리스로, 일부는 전통적인 마이크로서비스로 구성으로 수 있다.
  - **BAAS (BACKEND-AS-A-SERVICE)**
    주로 모바일 앱, 웹 앱에 쓰기 때문에 서비스로서의 모바일 백엔드(Mobile BaaS, MBaaS)로도 알려져 있다. 단일 웹페이지나 모바일 앱 기반의  
    서비스에서 필요한 서버 기능들을 사용하기 위해 이용하는 써드파티(Third Party) 애플리케이션, 혹은 클라우드 서비스이다.  
    *애플리케이션 개발 시 복잡한 백앤드(Back-End) 기능들을 개발자가 직접 개발하지 않고 클라우드 공급자가 제공하는 서비스를 이용해 쉽고 안정적으로  
    구현한다.* 예컨대 클라우드 제공업체가 인증 서비스와 추가 암호화, 클라우드 액세스 가능한 데이터베이스, 상세한 데이터 사용량 모니터링 등을  
    ‘완성해’ 제공하고, 개발자 및 서비스는 그것을 바탕에 둔 애플리케이션 및 서비스를 구성하는 것이다. 보통 클라우드 제공업체가 설정한 애플리케이션  
    프로그래밍 인터페이스(Application Programming Interface, API) 호출을 통해 액세스한다. 이러한 기능은 일반기능이며 클라우드 특성에 맞춘  
    최적화가 필요하기에, 프로젝트를 위해 새로 개발하는 것보다 클라우드 시스템에 통합되어 클라우드 공급자가 제공하는 것을 사용하는 편이 훨씬 간단하다.  
    <u>유명한 것으로는 Firebase, Auth0 등이 있다.</u>
    
  - **FAAS (FUNCTION-AS-A-SERVICE)**
    함수(로직)은 개발자가 설계하되 그것이 일반적인 서버가 아닌 클라우드 제공업체가 관리하는 클라우드 컨테이너에서 작동하는 경우를 의미한다.  
    함수를 개발자가 특정 프로젝트(서비스)를 위해 작성하기에 BaaS보다 높은 수준의 제어 기능을 포함한다. 즉, 보다 고도화되거나 특성화된 서비스  
    수행에 적합하다.
    확장성이 매우 뛰어나단 장점을 가지고 있다. FaaS를 사용하지 않을 경우 일반적으로 다양한 트래픽에 유연한 대응하기 위해 AWS의 Auto Scaling  
    같은 기술을 사용한다. 이를 통해 CPU 사용량, 네트워크 처리량에 따라 서버의 개수(=처리할 수 있을 트래픽의 양)를 증감하는 방식으로 대응한다.  
    그런데 FaaS를 사용하면 이 대응을 보다 정교하게 만들 수 있다. 특정 조건에 따라 자동으로 자원사용량을 가감하는 것이 아닌, 함수를 1초에 1개가  
    호출하면 자원소모(=컴퓨팅) 1개가 발생하고, 100,000,00 개가 호출되면 100,000,00 개의 자원을 소모하는 식으로 정교하게 트래픽 처리가  
    발생하게끔 만들 수 있다. 그리고 호출된 횟수만큼 클라우드 사용료를 내면 된다. 

#### \*장점과 단점
  1. 장점
    - 서버 관리가 필요 없다.
    - 유연한 확장성: 애플리케이션을 활용하여 자유자재로 확장을 구현할 수 있다.
    - 높은 가용성: 고정된 서버가 없음은 제한된 가용성이 아님을 의미합니다. 가용성을 위한 별도의 설계가 필요 없다.
    - 유휴 용량에 대한 비용: 사용하지 않는 것에 대해선 비용을 지불할 필요가 없습니다. 실행하지 않을 때는 비용이 발생하지 않는다.
    - 개발자 생산성을 높이고 운영 비용을 줄일 수 있다.
  2. 단점
    - 콜드스타트(Cold-Start): 빠른 응답이 필요한 제품(서비스)의 경우 서버리스로의 전환은 부적합할 수 있다.  
    이는 실행할 함수를 호출하기 위해 컨테이너가 실행되는 대기 시간이 존재하기 때문인데, 서버를 항시 가동하지 않는 서버리스의 특징에 기인한다.
    - 무상태(Stateless)적인 기능의 구현 불가: 작은 기능으로 잘게 나눠진 함수들은 요청마다 새로 기동하도록 호출되기 때문에 기동 전후의 상태를 공유할 수 없다.  
    또한 변수와 데이터의 공유가 불가능하며, 데이터를 로컬 스토리지에서 읽고 쓸 수 없다.
    - 벤더 종속의 문제: 함수가 사용할 수 있는 최대 메모리, 최대 처리 가능 시간 제약 등의 제약을 서버리스 서비스 벤더가 설정하며 서버리스 사용자 및 서버리스 기반의  
    서비스는 이에 종속된다. 이에 맞춰 벤더가 설정한 제약을 벗어나는 큰 기능은 잘게 나누어 구현해야 한다.
***
    <<3주차 회고록>>
    3주차를 회고하려고 보니 이번주 정말 힘들었던거 같다. 개인적으로 노션에 매일 한 줄씩 적는 다이어리가 있었는데,  
    그것도 딱 하루 기록했더라...그게 바로 5/26...그것도 한 줄로 요약할 수 있다.  
    "삽질의 한 주"
    나는 3주차를 시작하면서 주어진 강의를 완주하는 것을 목표로 꾸역꾸역했고, 과제를 수행할 밑바탕이 될 줄 알았는데,  
    전혀 아니였다.  
    나는 기초가 없었다. 자바스크립트, 리액트 기초 그 어느것 하나 제대로 이해하는게 없었다는 것을 6일 삽질한 끝에  
    완전히 인지했다.
    
  *이제 내가 실행 해야할 것*
 - [ ] 기초 강의(유튜브)부터 듣고 개념이해  
 - [ ] 모르는 키워드 구글링하면서 정리하기  
 - [ ] 과제를 할 때는 why?부분을 참고해서 잘 읽을 것(내가 무엇을 구현해야 하는지 파악 필요)
 - [ ] 구현하고자 하는 것을 정의하고 그 부분 공부(제공 강의, 구글링)하면서 구현하기  
 - [ ] TIL 작성하기(하루동안 내가 찾아보고 배운 것을 내 것으로 정리하기)

