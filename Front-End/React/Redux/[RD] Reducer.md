# Reducer
  > **Store 값의 상태를 변경시키는 함수**

  Redux에서 setState 역할을 가지고 있는 함수로, 매개변수로 원래 state값과 action을 받아 상태를 수정하는 함수이다.

  ## 생성
  ```js
  import { createStore } from "redux";
  import { Provider } from "react-redux";
  import App from "./App";
  
  // 이번에 추가된 부분
  const state = 0;
  const reducer = (state, action) => {
    switch(action.type {
      case "INCREASE":
        return state + 1;
      case "DECREASE":
        return state - 1;
      case "SET_NUMBER":
        return action.payload;
      default:
        return state;
    })
  }

  const store = createStore(reducer);

  root.render(
    <Provider store={store}>
      <App />
    </Provider>
  );
  ```