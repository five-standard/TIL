# LifeCycles
  > **React-Query의 라이프 사이클**

  React-Query의 라이프 사이클에 쓰이는 상태값들이다.

  ## Fresh
  API에서 받은 데이터가 가장 먼저 가지는 상태이다.  
  이 상태에서는 API 요청시 이 데이터가 그대로 반환된다.

  ## Fetching
  API를 날리고 기다리고 있는 상태이다.

  ## Stale
  staleTime이 지난 상태이다.  
  이 상태에서는 API 요청시 서버에서 데이터를 받아온다.

  ## Inactive
  쿼리가 실행된 컴포넌트가 unMount되었을 때의 상태로, cacheTime을 지날 때까지 데이터를 캐싱한다.  
  cacheTime이 지나기 전 까지는 컴포넌트가 mount되었을 경우 캐시된 데이터를 임시로 반환한다.
 
  ## Delete
  cacheTime이 지난 상태로, 가비지 컬렉터에 의해 메모리에서 데이터가 제거된다.