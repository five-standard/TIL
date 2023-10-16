# useQuery
  > **Axios로 따지자면, GET 요청에 쓰이는 기능**
  
  서버에서 데이터를 조회(GET)할 때 사용하는 기능이다.

  ```js
  import { useQuery } from '@tanstack/react-query';
  import { axios } from 'axios';

  function Example() {
    const { isLoading, error, data } = useQuery({
      queryKey: ['repoData'], // 나중에 동일한 쿼리를 불러올 떄 쓰인다.
      queryFn: () => // 실제로 호출하고자 하는 비동기 함수가 들어간다.
        axios.get('https://api.github.com/repos/tannerlinsley/react-query').then(
        (res) => res.json(),
      ),
    })

    if (isLoading) return 'Loading...' // 로딩중엔 여기서 멈춘다

    if (error) return 'An error has occurred: ' + error.message // 오류가 발생하면 여기서 멈춘다

    return (
      <div>
        <h1>{data.name}</h1>
        <p>{data.description}</p>
        <strong>👀 {data.subscribers_count}</strong>{' '}
        <strong>✨ {data.stargazers_count}</strong>{' '}
        <strong>🍴 {data.forks_count}</strong>
      </div>
    )
  }
  ```

  ## 동기적으로 실행
  옵션 값중 enabled를 사용하여 useQuery를 동기적으로 사용할 수 있다.  
  enabled에 대입된 값이 true가 되면 useQuery를 동기적으로 실행시킨다.  
  ```js
  const { data: nextTodo, error, isFetching } = useQuery(
    "nextTodos",
    fetchNextTodoList,
    { enabled: todoList }
  );
  ```

  ## 다중 실행
  한 번에 여러 useQuery를 사용하려면 useQueries로 묶어 사용하면 된다.  
  Promise.all()과 형태가 비슷하다.

  ```js
  const results = useQueries({
    queries: [
      { queryKey: ['post1', 1], queryFn: fetchPost, staleTime: Infinity},
      { queryKey: ['post2', 2], queryFn: fetchPost, staleTime: Infinity}
    ]
  })
  ```