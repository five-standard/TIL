# GRID
  > 페이지 구조를 잡기 위해 사용하는 CSS 속성.

  **그리드 컨테이너**와 **그리드 아이템**이 필요하s다.

  ## 용어
  <img src="https://studiomeal.com/wp-content/uploads/2020/01/03-2.jpg" alt="GRID의 형태 (by 1분코딩)">
  
  - **그리드 컨테이너 (Grid Container)**  
    Grid를 적용하는, Grid의 전체 영역.  
    위 코드중 `<div class=”container”></div>`가 Grid 컨테이너이다.
  - **그리드 아이템 (Grid Item)**  
    Grid 컨테이너의 자식 요소들.  
    이 아이템들이 Grid 규칙에 의해 배치된다.  
    위 코드중 `<div class=”item”></div>`들이 Grid 아이템이다.
  - **그리드 트랙 (Grid Track)**  
    Grid의 행(Row) 또는 열(Column)
  - **그리드 셀 (Grid Cell)**  
    Grid의 한 칸 (Grid 갭으로 둘러쌓여있다.)  
    `<div>`같은 요소들이 Grid 아이템이며, 이런 Grid 아이템 하나가 들어가는 칸이라고 볼 수 있다.
  - **그리드 라인(Grid Line)**  
    Grid 셀을 구분하는 선.
  - **그리드 번호(Grid Number)**  
    Grid 라인의 번호들.
  - **그리드 갭(Grid Gap)**  
    Grid 셀 사이의 간격.
  - **그리드 영역(Grid Area)**  
    Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이다.
  
  ## 속성 - 컨테이너
  - display: grid  
    컨테이너에 Grid 속성을 적용하는 것이 시작이다.
