# useEffect
  > **마운트, 업데이트, 언마운트시 동작되는 훅**
  
  컴포넌트가 Mount, Update, Unmount시 동작되는 훅이다.
  
  ## 사용하는 이유
  React의 생명주기를 관리하기 위해 사용한다.  
  여기서 생명 주기란, 컴포넌트의 Mount, Update, Unmount를 의미한다.

  ## 사용
  ```js
  useEffect(() => {
    console.log("useEffect");
    return () => {
      console.log("clean Up!"); 
    }
  }, [deps]) /* deps가 비어있다면 마운트 시에만 실행된다.
  deps에 변수가 들어있다면, 해당 변수의 업데이트 시에도 실행된다.
  return(클린업) 힘수가 존재한다면, 언마운트 시에도 실행된다. */
  ```

  ## 참고할 점
  useEffect는 컴포넌트 렌더링이 끝난 후에 실행된다.  
