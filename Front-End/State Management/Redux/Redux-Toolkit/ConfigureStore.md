# ConfigureStore
  > **Redux에서의 createStore와 비슷한 것**
  
  ```js

  // store.js
  import React from 'react';
  import { configureStore } from '@reduxjs/toolkit';
  import dataReducer from './data';

  export default configureStore({
    reducer: {
      data: dataReducer // 여기서 여러 개의 리듀서를 한번에 선언할 수 있다.
    },
    // middleware: ["미들웨어 배열이다."],
    // devTools: 개발자도구 사용 여부를 설정한다.,
    // preloadedState: "초기 state들을 저장한다.",
    // enhaners: ["enhancer 배열이다."],
  })

  // index.js
  import React from 'react';
  import ReactDOM from 'react-dom';
  import App from './App';
  import store from './redux/store';
  import { Provider } from 'react-redux';

  ReactDOM.render(
    <React.StrictMode>
      <Provider store={store}>
        <App />
      </Provider>
    </React.StrictMode>,
    document.getElementById('root')
  );
  ```