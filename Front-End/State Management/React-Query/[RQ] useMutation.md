# useMutation
  > **Axios로 따지자면, POST, PATCH, DELETE 요청에 쓰이는 기능**
  
  서버에서 데이터를 수정(POST, PATCH, DELETE)할 때 사용하는 기능이다.

  ```js
  import { useMutaion } from '@tanstack/react-query';
  import { axios } from 'axios';

  function Func(data) {
    return await axios.post('/test', data);
  }

  function Example() {
    const { mutate, isLoading, isError, error, isSucces } = useMutation(Func);

    if (isLoading) return 'Loading...' // 로딩중엔 여기서 멈춘다

    if (error) return 'An error has occurred: ' + error.message // 오류가 발생하면 여기서 멈춘다

    return (
      <div>
        <h1>test success</h1>
      </div>
    )
  }
  ```