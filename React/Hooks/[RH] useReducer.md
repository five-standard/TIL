# useReducer
  > **현재 상태와 액션 객체를 파라미터로 받아와서 새 상태를 반환하게 해주는 훅.**
  
  현재 상태와 액션 객체를 파라미터로 받아와서 새 상태를 변환하게 해주는 훅이다.  
  useState를 사용한 상태 변경을 분리할 때 사용된다.

  ## 사용하는 이유
  useState의 setState함수를 여러번 사용하지 않아도 된다는 점, 로직 분리를 통해 다른 함수에서도 손쉽게 재사용할 수 있다는 점 떄문이다.  
  물론 코드량이 조금 늘어나긴 하지만, 위의 장점을 통해 코드를 체계적으로 관리할 수 있게 된다.

  ## 사용
  ```js
  function reducer(state, action) {
    switch(action.type) {
      case 'IN':
        return state + 1;
      case 'DE':
        return state - 1;
      default:
        return state:
    } //state는 값, action은 dispatch의 type을 의미한다.
  }

  function Count() {
    const [num, dispatch] = useReducer(reducer, 0); //0은 기본값을 의미한다.

    const onIncrease = () => {
      dispatch({ type: 'IN' });
    } /* dispatch를 통해 action을 보낸다.
    참고로 dispatch를 통해 값을 보내는 것도 가능하다.
      
      dispatch({ 
        type: 'Action',
        propOne,
        propTwo      
      })

    와 같은 방식으로 보낼 수 있다 */

    const onDecrease = () => {
      dispatch({ type: 'DE' });
    }

    return <>
      <h1>{num}</h1>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>
    </>
  }
  ```