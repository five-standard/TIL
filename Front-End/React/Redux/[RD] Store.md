# Store
  > **전역 값이 저장되는 저장소**
  
  Redux를 통해 전역 상태관리를 하기 위해선 먼저 Store를 생성해야 한다.

  Store에서 관리되는 값은 안정성으로 인해 일반적인 방법으로 수정할 수 없으며, 정해진 방식으로만 가져와야 한다.

  ## 생성
  createStore 메소드를 통해 Store 객체를 생성하면 된다.
  ```js
  import { createStore } from "redux";
  import { Provider } from "react-redux";
  import App from "./App";

  // Store 생성 함수
  const store = createStore();
  
  root.render(
    <Provider store={store}>
      <App />
    </Provider>
  );
  ```