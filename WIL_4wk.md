### 라이프사이클(클래스형 vs 함수형), react hooks
***

  #### 클래스형 컴포넌트와 함수형 컴포넌트
  리액트 컴포넌트는 클래스형 컴포넌트 또는 함수형 컴포넌트로 작성될 수 있다.

    - **클래스형 컴포넌트**는 상태값을 가질 수 있고, 리액트 컴포넌트의 생명 주기 함수를 작성할 수 있다. 그러나 **함수형 컴포넌트**는 이 모든 일을 할 수 없다. 이 둘의 차이점은 상태값과   LifeCycle를 가질 수 있느냐 없느냐이다.
  ##### (참고)리액트 버전 16.8부터 훅(Hook)이 등장하면서 함수형 컴포넌트에서도 상태값과 생명 주기 함수 코드를 작성 할 수 있게 되었다.
      
![스크린샷 2022-06-05 오후 11 12 31](https://user-images.githubusercontent.com/105087933/172054808-524a92a2-d81b-488d-8376-76589b57d244.png)

    **클래스형 컴포넌트**
      - class 키워드가 필요하다
      - Component로 상속 받아야 한다
      - render() 함수를 사용해서 JSX를 반환해야 한다
      - props를 조회할 때 this 키워드를 사용한다
      - defaultProps 설정 시 클래스 내부에 static 키워드와 함께 선언한다

    **함수형 컴포넌트**
      - 클래스형 컴포넌트보다 선언하기 수월하다
      - 클래스형 컴포넌트보다 메모리 자원을 덜 사용한다
      - state, 라이프사이클 API를 사용할 수 없다 -> React Hooks을 통해 해결 할 수 있게 되었다.  
       *참고 : https://velog.io/@seong-dodo/React-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-vs-%ED%95%A8%EC%88%98%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8
***

#### \*라이프사이클
![image](https://user-images.githubusercontent.com/105087933/172054973-44462b18-178b-4877-9915-884332357548.png)

- LifeCycle Method는 컴포넌트가 브라우저상에 나타나고, 업데이트되고, 사라지게 될 때 호출되는 메서드들이다. 컴포넌트 라이프 사이클은 크게 **마운트 - 업데이트 - 언마운트**로 단계로 나뉜다.
  실제 프로덕션에서 아래 여섯가지 위주로 life cycle을 관리한다.
    🔘 constructor
    🔘 render
    🔘 componentDidMount
    🔘 shouldComponentUpdate
    🔘 componentDidUpdate
    🔘 componentWillUnmount
    
  - **마운트 단계 (초기화 단계)** 는 최초에 컴포넌트 객체가 생성될 때 한 번 수행된다. 마운트될 때 발생하는 생명주기들은 
    1️⃣ constructor, 2️⃣ getDerivedStateFromProps, 3️⃣ render, 4️⃣ componentDidMount가 있다.
  - **업데이트 단계** 는 초기화 단계와 소멸 단계 사이에서 반복해서 수행된다. 컴포넌트의 속성값 또는 상태값이 변경되면 업데이트 단계가 수행된다. 이 단계에서 실행되는 생명 주기 메서드의 호출 순서는 아래와 같다.
    1️⃣ getDerivedStateFromProps -> 2️⃣ shouldComponentUpdate -> 3️⃣ render -> 4️⃣ getSnapshotBeforeUpdate -> 5️⃣ componentDidUpdate
  - **언마운트 단계 (소멸 단계)** 에서는 컴포넌트가 화면에서 사라지기 직전에 아래 메서드가 호출된다. 
     componentWillUnmount 가 호출된다.
  
    참고 : https://react.vlpt.us/basic/25-lifecycle.html
    https://ko.reactjs.org/docs/react-component.html#constructor
  
***

### \*리액트 훅
 - React 16.8에 새로 추가된 기능으로 class를 작성하지 않고도 state와 다른 React의 기능들을 사용할 수 있게 해준다.

  #### \*State Hook

  - **useState** : 컴포넌트에서 보여줘야 하는 내용이 사용자 인터랙션에 따라 바뀌어 바로 UI가 업데이트 된다.
  → state에 react를 할 수 있게 해준다. useState 함수를 사용해보게 되는데, 이게 바로 리액트의 Hooks 중 하나이다.
    (예제)![스크린샷 2022-06-05 오후 11 32 38](https://user-images.githubusercontent.com/105087933/172055680-a6fc640c-9caa-4a63-9383-4768d34ab071.png)

  #### \*Effect Hook
  - **useEffect** : 클래스 컴포넌트의 생명주기 메소드 componentDidMount(), componentDidUpdate, componentWillUnmount()를 통합한 것과 같은 API로 side effect를 발생하는 작업을 수행하는 훅 API이다.
  - *useState는 변수를 추척해 변화가 생긴다면 재렌더링하는 기능이라면, useEffect는 변수를 추적해 변화가 생기면 어떠한 기능을 수행한다.*
  -  useEffect는렌더링, 혹은 변수의 값 혹은 오브젝트가 달라지게 되면, 그것을 인지하고 업데이트를 해주는 함수이다. useEffect는 콜백 함수를 부르게 되며, 렌더링 혹은 값, 오브젝트의 변경에 따라 어떠한 함수 혹은 여러 개의 함수들을 동작시킬 수 있다.
  (예제){![스크린샷 2022-06-05 오후 11 45 21](https://user-images.githubusercontent.com/105087933/172056199-5f22f174-0003-48fe-a269-6570694337e3.png)
    참고 링크 : https://gist.github.com/ninanung/0ea87bc3d14ed8b1f9e7488561a4b910
    (참고) effect를 실행하고 이를 정리(clean-up)하는 과정을 (마운트와 마운트 해제 시에)딱 한 번씩만 실행하고 싶다면, 빈 배열([])을 두 번째 인수로 넘기면 된다. 이렇게 함으로써 React로 하여금 여러분의 effect가 prop이나 state의 그 어떤 값에도 의존하지 않으며 따라서 재실행되어야 할 필요가 없음을 알게 하는 것이다. 이는 의존성 배열의 작동 방법을 그대로 따라서 사용하는 것일 뿐이며 특별한 방법인 것은 아니다. 빈 배열([])을 넘기게 되면, effect 안의 prop과 state는 초깃값을 유지하게 된다. 빈 배열([])을 두 번째 인수로 넘기는 것이 기존에 사용하던 componentDidMount와 componentWillUnmount 모델에 더 가깝지만, effect의 잦은 재실행을 피할 수 있는 더 나은 해결방법이 있다. 또한 React는 브라우저가 다 그려질 때까지 useEffect의 실행을 지연하기 때문에 추가적인 작업을 더하는 것이 큰 문제가 되지는 않습니다.

  - **useReducer**는 useState보다 더 다양한 컴포넌트 상황에 따라 다양한 상태를 다른 값으로 업데이트 해주고 싶을 때 사용하는 Hook이다. 
  ```javascript
  const [state, dispatch] = useReducer(reducer, initialArg, init);
  ```
  - (state, action) => newState의 형태로 reducer를 받고 dispatch 메서드와 짝의 형태로 state를 반환한다. 하윗값이 복잡한 정적 로직을 만들거나, 다음 state가 이전 state에 의존적인 경우 보통 useState 대신 useReducer를 사용한다. 
  - 또한 useReducer는 자세한 업데이트를 트리거 하는 컴포넌트의 성능을 최적화 할 수 있는데, 이것은 Callback 대신 dispatch를 전달할 수 있기 때문이다.
   
  - **useMemo** 를 사용하면 함수형 컴포넌트 내부에서 발생하는 연산을 최적화할 수 있다. 이 Hook은 메모이제이션 된 값을 반환한다. useMemo는 의존성이 변경되었을 때만 메모이제이션 된 값을 다시 계산한다. 이 최적화는 모든 렌더링 시 고비용 계산을 방지하게 해 준다.  
  ```javascript
  const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
  ```
  useMemo로 전달된 함수는 렌더링 중에 실행이 된다. 따라서 렌더링 중에 하지 않는 작업은 이 함수 내에서 할 수 없다.
  
  - **useCallback** 은 메모이제이션 된 콜백을 반환한다. 주로 렌더링 성능을 최적화 해야 하는 상황에서 사용하는데, 이 Hook을 통해서 이벤트 핸들러 함수를 필요할 때만 생성할 수 있다.  
  ```javascript
  const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
  );
  ```
  인라인 콜백과 그것의 의존성 값의 배열을 전달하면 useCallback은 콜백의 메모이제이션된 버전을 반환한다. 그 메모이제이션된 버전은 콜백의 의존성이 변경되었을 때만 변경된다. 이는 불필요한 렌더링을 방지하기 위해 참조의 동일성에 의존적인 최적화된 자식 컴포넌트에 콜백을 전달할 때 유용하다. useMemo와 비슷한 역할을 하고 useCallback은 결국 useMemo로 함수를 반환하는 상황에서 더 편하게 사용할 수 있는 훅이다. 숫자, 문자열, 객체 처럼 일반 값을 재사용하려면 useMemo를 사용하고, 함수를 재사용하려면 useCallback을 사용한다.  
  
  - **useRef** 는 함수형 컴포넌트에서 ref를 쉽게 사용할 수 있도록 해준다. useRef는 .current 프로퍼티로 전달된 인자(initialValue)로 초기화된 변경 가능한 ref 객체를 반환한다.  
  ```javascript
  const refContainer = useRef(initialValue);
  ```  
  useRef()가 순수 자바스크립트 객체를 생성하기 때문이다. useRef()와 {current: ...} 객체를 생성하는 것의 차이점은 useRef는 매번 렌더링을 할 때 동일한 ref 객체를 제공한다는 점이다.
  
  - **useContext** 는 context 객체(React.createContext)를 받아 그 context의 현재 값을 반환한다. context의 현재 값은 트리 안에서 이 Hook을 호출하는 컴포넌트의 가장 가까이에 있는 <MyContext.Provider>의 value prop에 의해 결정된다.  
  ```javascript
  const value = useContext(MyContext);
  ```  
  컴포넌트에서 가장 가까운 <MyContext.Provider>가 갱신되면 useContext는 <MyContext.Provider>에게 전달된 가장 가까운 context value를 사용하여 렌더러를 트리거 한다.상위 컴포넌트에서 React.memo나 shouldComponentUpdate를 사용하더라도 useContext를 사용하고 있는 컴포넌트 자체에서부터 다시 렌더링이 된다. 항상 인자는 context 객체 그 자체여야 한다.  

useContext를 호출한 컴포넌트는 context 값이 변경되는 항상 리렌더링 된다. 따라서 이 비용이 많이 들면 메모이제이션을 통해 최적화를 할 수도 있다.  
    참고 : https://devowen.com/312
***

  <<4주차 회고록>>
    4주차를 회고하려고 보니 3주차와 이어서 정말 힘들다. 3주차를 회고하고 방법을 바꾸어서 개념 정리 -> 새로운 지식 습득(리덕스) -> 구글링 하면서 개념정리
    하면 할수록 모르는 것 투성이고, 나름 정리했다고 했는데 빈틈이 꽤 많았다.
    지난추에 찾아서 공부하고 정리했던 개념이 제대로 정리가 안되어 있었다 보니 또 다시 그 내부를 들여다 보게 되었고, 뭔가 쌓이는 느낌이 아니라 흝어지는 느낌이 성과가 하나도 없는 느낌이다.
    이번주차 과제도 거의 이 코드 저 코드를 복붙하고 강의 자료를 복붙하며 추가하기만 겨우 구현했다. 지난주차부터 이번주차까지 내가 무언가를 만든 느낌이 아니라서 재미도 없고 마음도 힘들다.
    이제 새로 시작하는 리액트 심화주차에 난 드디어 무언가를 만들어 보려고 한다. 이번주차 때 무언가를 만들지 않으면, 미니 프로젝트 자신이 없을 것 같다. 화이팅!
    
    *이제 내가 실행 해야할 것*
 - [ ] 제공 강의 듣기
 - [ ] 개인과제 구현 할 기능 정리
 - [ ] 과제를 할 때는 why?부분을 참고해서 잘 읽을 것(내가 무엇을 구현해야 하는지 파악 필요)
 
