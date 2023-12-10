# React-Redux
  > **객체 전달, state 업데이트 Hook을 전달하는 라이브러리**
  
  Redux를 더 편하게 사용하기 위해 나론 라이브러리이다.  
  useSelector, useDispatch 등을 지원한다.

  ## UseSelector
  store의 state에 접근하는 hook이다.  
  useState의 state처럼 활용하면 된다.

  ```js
  import { useSelector } from 'react-redux';

  export const Counter = () => {
    const count = useSelector((state) => state.counter);
    console.log(count);
    return <></>
  }
  ```

  ## UseDispatch
  action을 reducer로 보내는 hook이다.  
  useState의 setState처럼 쓴다.

  ```js
  import { useDispatch } from 'react-redux';

  export const Counter = () => {
    const dispatch = useDispatch();
    
    const increase = () => {
      dispatch({ type: 'INCREASE' };)
    }

    const decrease = () => {
      dispatch({ type: 'DECREASE' };)
    }

    return <></>
  }
  ```