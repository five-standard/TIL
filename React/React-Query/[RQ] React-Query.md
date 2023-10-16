# React-Query
  > **Fetching, Caching, 서버 데이터와의 동기화 등을 지원하는 라이브러리**
  
  Fetch, Cache, 서버 데이터 동기화 등을 지원하는 라이브러리이다.  
  Axios와 함께 서버 데이터를 관리할 때 사용할 수 있다.
  
  ## 장점
  - ### Caching을 통한 애플리케이션 최적화
  - ### 데이터 중복 요청을 제거
  - ### 데이터 Updating 지원
  - ### 비동기 API를 선언적으로 관리
  
  ## 캐싱
  앞서 말했듯이, React-Query는 데이터 캐싱을 지원한다.  
  이를 통해 동일한 데이터에 대한 데이터 호출을 방지하고, API 콜을 줄여 서버의 부하를 줄일 수 있다.  

  ### 갱신
  여기서 캐싱된 데이터가 최신의 것인지 알 수 없기 때문에, 서버에서 데이터가 변경됬다면 사용자는 과거의 데이터를 보는 오류가 발생하게 된다.  

  React-Query에서는 이 문제를 staleTime과 cacheTime을 통해 해결했다.
  
  - ### staleTime  
    데이터가 fresh -> stale 상태로 변하는 데 걸리는 시간이다.  
    fresh 상태라면 Refetch 트리거가 발생해도, Refetch되지 않는다.  
    기본값으로 0이 설정되어있어, 따로 설정하지 않으면 Refetch 트리거가 발생했을 때 무조건 Refetch된다.

  - ### cacheTime
    데이터가 inactive한 상태일 때 캐싱된 상태로 남아있는 시간이다.
    특정 컴포넌트가 unMount(화면에서 사라질 때)되면 해당 데이터가 inactive상태로 바뀌며, cacheTime만큼 유지된다.  
    이후 데이터는 가비지 콜렉터로 수집되어 제거된다.  
    만약 캐싱된 상태에서 다시 해당 컴포넌트가 mount되면, 새 데이터를 fetch해오는 동안, 캐싱된 데이터를 임시로 보여준다.

  ## 설치 & 설정
  - **npm install react-query**  

  - ```js
    import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
    const queryClient = new QueryClient()

    function App() {
      return
        <QueryClientProvider client={queryClient}>
          <Components props={...children} />
        </QueryClientProvider>
    }
    ```
  