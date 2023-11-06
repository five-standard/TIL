# useRef
  > **DOM을 직접 다루게 해주는 훅**
  
  리액트에서 DOM을 직접 다루고 싶을 떄 사용하는 훅이다.
  클래스형 컴포넌트에선 콜백 함수나 React.createRef라는 함수를 사용한다.
  
  ## 사용하는 이유
  리액트에선 Virtual DOM을 사용하기 때문에, DOM을 직접 건드리지 않는 것이 좋다.  
  하지만 DOM노드, 요소, React 컴포넌트 주소 값이 필요할 때가 있는데, 이런 상황에서 useRef를 사용하면 직접 해당 값들을 참조할 수 있다.

  ## 사용
  ```js
  const Hello = useRef();
  
  const World = () => {
    Hello.current.focus();
  } /* current라는 속성에 반환 인자를 저장한다. 
  현재 상황에선 <input> 요소가 저장되있다. */

  return <>
    <input ref={Hello}>
  </>
  ```