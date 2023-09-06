# GRID
  > ㅤ  
  > **페이지 구조를 잡기 위해 사용하는 CSS 속성.**  
  > ㅤ

  **그리드 컨테이너**와 **그리드 아이템**이 필요하다.

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

  ## 속성들
  - **display: grid**  
    컨테이너에 Grid 속성을 적용하는 것이 시작이다.
  - **grid-template-rows(행)**  
    **grid-template-columns(열)**
    Grid 트랙의 크기들을 지정해주는 속성이다.  
    여러 단위를 사용하거나 섞어 쓸 수 있다.
    - **Repeat 함수**  
      반복되는 값을 자동으로 처리할 수 있는 함수.
    - **minmax 함수**  
      최솟값과 최댓값을 지정할 수 있는 함수.
    - **auto-fill과 auto-fit**  
      셀을 최대한 채우는 속성
  - **row-gap**  
    **column-gap**  
    **gap**  
    그리드 셀 사이의 간격을 설정한다.
  - **grid-auto-columns**  
    **grid-auto-rows**  
    그리드의 형태를 자동으로 정의한다.
  - **grid-column-start**  
    **grid-column-end**  
    **grid-column**  
    **grid-row-start**  
    **grid-row-end**  
    **grid-row**  
    각 셀의 영역을 지정한다.
  - **grid-template-areas**  
    각 영역에 이름을 붙이고, 그 이름을 이용하여 배치해준다.  
  - **grid-auto-flow**  
    아이템이 자동 배치되는 흐름을 결정하는 속성이다.
  - **align-items**  
    아이템들을 세로 방향으로 정렬한다.
  - **justify-items**  
    아이템들을 가로 방향으로 정렬한다.
  - **align-content**  
    모든 아이템의 높이를 합한 값이 컨테이너의 높이보다 작을 때, 아이템들을 통쨰로 세로 정렬한다.
  - **justify-content**  
    모든 아이템의 너비를 합한 값이 컨테이너의 너비보다 작을 때, 아이템들을 통쨰로 가로 정렬한다.
  - **align-self**  
    특정 아이템을 세로 방향으로 정렬한다.
  - **justify-self**  
    특정 아이템을 가로 방향으로 정렬한다.
  - **order**  
    아이템의 시각적 나열 순서를 결정하는 속성이다.
    작은 숫자일 수록 먼저 배치된다.
  - **z-index**  
    Z축 정렬을 해 주는 속성이다.  
    수가 클 수록 위로 올라온다.

## Grid 연습 사이트
  https://cssgridgarden.com/#ko  
  해당 페이지에서 **grid 속성들**을 사용해 볼 수 있다.