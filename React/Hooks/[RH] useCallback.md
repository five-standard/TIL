# useCallBack
  > **useMemo 기반의 함수 재활용을 위한 훅**
  
  useMemo를 기반으로 만들어진 훅으로, 특정 함수를 새로 만들지 않고 재사용하고 싶을 떄 사용하는 훅이다.

  ## 사용하는 이유
  컴포넌트가 리렌더링될때마다 컴포넌트 내부의 함수들이 새로 만들어진다.  
  함수를 새로 선언한다고 엄청난 리소스를 사용하진 않지만, 추후 props가 바뀌지 않았을 때 리렌더링 없이 컴포넌트를 재사용하는 최적화 작업에 필요하다.
  
  ## 사용
  ```js
  const hello = useCallback(() => {
    console.log(deps, "useCallback");
  }, [deps])
  ```
  ```js
  const hello = useMemo(() => () => {
    console.log(deps, "useCallback");
  }, [deps]
  ) // useMemo를 사용하여 작성할 경우
  ```

  참고로 deps에 함수에서 사용하는 값과 props로 받아온 함수를 넣어야 한다.  
  넣지 않았다면, 함수가 해당 값들을 참조할 때 최신 값을 참조했다고 보장할 수 없다.
  