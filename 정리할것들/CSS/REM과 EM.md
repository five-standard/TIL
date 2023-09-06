# REM과 EM
  > ㅤ  
  > **반응형을 위한 CSS 상대단위**  
  > ㅤ
  
  **페이지의 폰트 크기 값**에 따라 값이 변한다는 공통점이 있다.  
  em은 사용되는 요소의 폰트 크기에 따라 값이 달라지며, rem은 html의 폰트 크기에 따라 달라진다.  
  **(참고로 1em은 1*(font-size)px, 1rem은 1*(html font-size)px와 크기가 같다.)**

  ### em
    div {
      font-size: 20px;
      width: 10em; /* 200px */
    }

  ### rem
    div {
      font-size: 20px;
      width: 10em; /* 160px */
    }