# useMemo
  > **연산된 값을 재사용할 수 있게 해주는 훅**
  
  연산된 값을 재사용할 수 있게 해주는 훅이다.
  
  ## 사용하는 이유
  성능 최적화를 하기 위해서이다.  
  특히 특정 값에 변화가 있을 때만 작동되야 하는 함수가 있다면, 불필요한 리렌더링이 발생할 수 있다.  

  ## 사용
  ```js
  const Hello = useMemo(() => function(props), [props]);
  //props가 변경될 때애만 함수가 실행되고, Hello라는 변수의 값이 변경된다.
  
  return <>
    <h1>{Hello}</h1>
  </>
  ```

  ## 참고할 점
  useMemo의 Memo는 <b>"memoized"</b>라는 단어를 의미한다.  
  또한 useMemo를 기반으로 <b>useCallback</b>이라는 함수가 존재한다.