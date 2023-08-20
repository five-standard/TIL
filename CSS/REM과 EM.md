<h1>REM과 EM</h1>

<h2>rem과 em</h2>
<div>
  rem과 em은 css의 상대단위이다. <br />
  <b>페이지의 폰트 크기 값</b>에 따라 값이 변한다는 공통점이 있다. <br/>
  em은 사용되는 요소의 폰트 크기에 따라 값이 달라지며, rem은 html의 폰트 크기에 따라 달라진다. <br />
  <b>(참고로 1em은 1*(font-size)px, 1rem은 16px와 크기가 같다.)</b>

  <h3>em</h3>
  <div>

    div {
      font-size: 20px;
      width: 10em; /* 200px */
    }

  </div>

  <h3>rem</h3>
  <div>

    div {
      font-size: 20px;
      width: 10em; /* 160px */
    }

  </div>
</div>