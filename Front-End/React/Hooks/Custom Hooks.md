# Custom Hooks
  > **내가 직접 만드는 React Hooks**

  반복되는 로직을 쉽게 재사용하기 위해 직접 훅을 제작하는 경우도 있는데, 이를 커스텀 훅이라 한다.  

  ## 제작 방법
  방법 자체는 간단하다.  
  파일과 함수의 이름을 use로 시작하는 이름으로 설정하고, 그 안에서 다른 hooks를 사용하여 원하는 기능을 구현하면 된다.  
  그 후 컴포넌트에서 사용하고 싶은 값들을 반환해주면 끝이다. 

  ## 예시
  ```js
  // useInputs.js
  import { useState, useCallback } from 'react';

  function useInputs(initialForm) {
    const [form, setForm] = useState(initialForm);
    // change
    const onChange = useCallback(e => {
      const { name, value } = e.target;
      setForm(form => ({ ...form, [name]: value }));
    }, []);
    const reset = useCallback(() => setForm(initialForm), [initialForm]);
    return [form, onChange, reset]; //이 값들이 initialForm 안에 들어가게 된다.
  }

  export default useInputs;
  ```

  ```js
  // index.js
  function index = () => {
    import useInputs from "useInputs.js";

    const [{ username, email }, onChange, reset] = useInputs({
      username: '',
      email: ''
    });

    return (
      <>
        <Components
          username={username}
          email={email}
          onChange={onChange}
          reset={reset}
        />
      </>
    )
  }
  

  ```