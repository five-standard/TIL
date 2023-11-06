# Action
  > **Reducer의 행동을 정하는 객체**

  Reducer 함수로 전달되는 객체로, 무조건 type이라는 키를 가지고 있어야 하며 그 외의 필요한 데이터를 payload로 가지고 있어야 한다.

  ## 생성
  ```js
  import { createStore } from "redux";
  import { Provider } from "react-redux";
  import App from "./App";
  
  // 이번에 추가된 부분
  export const increase = () => {
    return {
      type: "INCREASE"
    }
  }

  export const decrease = () => {
    return {
      type: "DECREASE"
    }
  }

  export const setNumber = (number) => {
    return {
      type: "SET_NUMBER",
      payload: number // Payload를 통해 값을 넘기게 된다.
    }
  }

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