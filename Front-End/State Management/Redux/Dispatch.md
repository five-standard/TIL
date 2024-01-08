# Dispatch
  > **action을 발생시키는 것**

  action 객체를 통해 상태를 업데이트시키는 데 쓰이는 메소드이다.  
  정확히는 action을 발생시키는 것이라고 보면 된다.

  ```js
  import { createStore } from "redux";
  import { Provider } from "react-redux";
  import App from "./App";

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

  // 이번에 추가된 부분
  const action = () => {
    store.dispatch(increase());
  } // 기본값은 0이나, action 함수를 실행시킬 때마다 값이 1씩 올라간다.

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
      <App onClick={action}/>
    </Provider>
  );
  ```
  ```