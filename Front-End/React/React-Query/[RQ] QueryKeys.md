# QueryKeys
  > **쿼리 캐싱을 관리하기 위해 사용하는 고유한 값**

  React-Query에서 쿼리 캐싱을 관리하기 위해 사용하는 고유한 값이다.  
  
  ## 규칙
  - ### 배열이어야 한다
    Tanstack-Query (V4)로 넘어오면서 변경된 점으로, QueryKey는 무조건 배열이어야만 한다.  
    ``const Query = useQuery(["key"], queryFn, enabled)`` - 쿼리키가 하나인 경우  
    ``const Query = useQuery(["key", props], queryFn, enabled)`` - 쿼리키가 여러개인 경우  
    ``const Query = useQuery(["key", { props, keyData, query }], queryFn, enabled)`` - 쿼리키가 여러개인 경우 (묶인 경우) 
     
  - ### 기본 작성 규칙
    - QueryKey의 값은 string키를 먼저 작성한다
    - string key는 여러개를 지정할 수 있으나, data는 고유하다
    - query에 필요한 정보 (queryFn이 참조하는 값 등)는 string key 뒤에 작성한다.