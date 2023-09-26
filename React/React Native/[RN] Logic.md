# Logic
  React Native는 **Native 부분과 JavaScript 부분**으로 나뉘어져있다.  
  - **Native 부분**에선 앱의 UI 렌더링, 네이티브 기능 실행 등을 담당한다.  
  - **JavaScript 부분**에선 비즈니스 로직, 뷰 표시 방식 지정 등을 담당한다.

  ## Native Bridge
  React Native에는 Native 코드와 Javascript 코드의 소통을 위한 브릿지가 존재한다.  
  **Native Bridge**가 바로 그것으로, JSON 객체 형태를 통해 정보를 전달하게 도와준다.  
  다만 이 Native Bridge를 과하게 사용하면 병목현상이 생길 수 있으니, 최소한으로 사용해야 한다.

  ### Deadline
  스마트폰의 프레임에 맞춰 애니메이션을 생성하지 않으면, 프레임 드랍이 발생한다.  
  이를 **Deadline**이라고 한다.  
  
  예를 들어, 아이폰은 **1초에 60프레임**을 표시한다.  
  이를 맞추기 위해, **16.67ms** 안에 하나의 프레임을 생성해야 한다.  
  안드로이드는 더 많은 프레임을 표시하는 경우도 많은데, 이에 맞추지 않으면 프레임 드랍이 발생하게 된다.

  ## JS Thread
  번들된 Javascript 코드들을 실행하며, 이벤트 루프가 끝날때마다 Main Thread로 관련 정보를 전달한다.  
  참고로 React 기반이기 때문에, 최적화된 **Diffing 알고리즘**을 사용하여 최소한의 정보만 Bridge로 넘겨진다.

  ### Diffing Algorithm
  React는 실제 DOM 노드가 아닌, **virtual DOM**을 사용하여 UI를 정의한다.  
  이 virtual DOM을 사용하여 최소한의 변경사항을 파악하여 리렌더링한다.  
  이 변경사항 파악 알고리즘이 **diffing 알고리즘**이다.  

  참고로 React는 트리 레벨 별 비교 작업을 수행하며, 이 작업의 시간복잡도는 **O(n)**에 가깝다고 한다.  
  보통 어플리케이션에서 컴포넌트 트리의 레벨은 변경되지 않는 다는 점을 이용한 방법을 쓴다.

  ### Rendering
  컴포넌트 안에서 setState를 호출하면, React는 이 컴포넌트를 ***dirty***하다고 표시한다.  
  그리고 이벤트 루프가 끝날 때마다 **컴포넌트들의 dirty 여부를 확인**하고, 렌더링을 진행한다.  
  여기서 자식 컴포넌트들에 대한 virtual DOM이 생성되는데, 상태 변경이 없었어도 **render 메소드**가 실행된다.  

  ![](https://velog.velcdn.com/images%2Fkoreanhole%2Fpost%2Fc2413904-80be-49bf-8e05-ece1d662a4fe%2F2.png)
  
  ## Main Thread(UI Thread)
  어플리케이션이 시작되자 마자 실행되며, UI를 렌더링하고, JS Thread를 실행한다.  
  JS Thread의 이벤트 루프가 끝날때마다 전송되는 메시지들을 해석하여 UI로 표시한다.  
  또한 사용자들의 UI 이벤트들(press, touch 등)을 받아 JS Thread로 넘겨준다. 

  ## 참고자료
  ### <a href="https://velog.io/@koreanhole/React-Native%EC%9D%98-%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC">React의 작동 원리</a>  

  ### <a href="https://www.codementor.io/@saketkumar95/how-react-native-works-mhjo4k6f3">Performance Overview · React Native</a>