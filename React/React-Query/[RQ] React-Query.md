# React-Query
  > Fetching, Caching, 서버 데이터와의 동기화 등을 지원하는 라이브러리
  
  Fetch, Cache, 서버 데이터 동기화 등을 지원하는 라이브러리이다.  
  Axios와 함께 서버 데이터를 관리할 때 사용할 수 있다.
  
  ## 장점
  - ### Caching을 통한 애플리케이션 최적화
  - ### 데이터 중복 요청을 제거
  - ### 데이터 Updating 지원
  - ### 비동기 API를 선언적으로 관리
  
  ## 설치 & 설정
  - **npm install react-query**  
  
  - ```js
    import { QueryClient, QueryClientProvider } from 'react-query'
    const queryClient = new QueryClient()

    function App() {
      return
        <QueryClientProvider client={queryClient}>
          <Components props={...children} />
        </QueryClientProvider>
    }
    ```
  