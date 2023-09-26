# Diffing
  > **React의 비교 알고리즘**
  
  리액트의 트리 비교 알고리즘이다.  
  해당 알고리즘은 트리를 비교할 때, 두 Element의 루트 Element부터 비교한다.  
  이후의 동작은 Element의 타입에 따라 달라진다.

  ## Element의 타입이 다를 때
  이전 트리를 버리고, 새로운 트리를 구축한다.  
  예시로 <b>`<a> -> <img>, <button> -> <div>`</b>등이 있다.  
  
  ## Element의 타입이 같고, 속성이 다를 때
  동일한 내역은 유지하고, 변경된 속성들만 갱신한다.  
  예시로, 아래 Element를 비교하면 className만 변경된다.
  ```js
    <div className="before" title="stuff" />

    <div className="after" title="stuff" />
  ```

  ## Element의 타입이 같을 떄
  State가 그대로 유지된다.

  ## 자식이 바뀌었을 때
  동시에 두 리스트를 순회하며 차이점이 있을 때, 해당 부분만 재귀가 처리한다.
  하지만 첫 자식부터 비교하기 떄문에, 첫 자식으로 Element를 추가할 때 성능이 좋지 않다.  

  이를 해결하기 위해 리액트에선 **Key**를 사용한다.  
  자식들이 Key를 가지고 있다면, 기존 트리와 이후 트리의 자식이 일치하는지 확인한다.  
  만약 아래 예시의 맨 앞 리스트에 값을 추가하고 싶다면, **2015보다 작은 값을 넣기만 하면 된다.**
  ```js
  <ul>
    <li key="2015">OLD<li>
    <li key="2016">NEW<li>
  </ul>

  -------------->

  <ul>
    <li key="2014">SUPER_OLD<li>
    <li key="2015">OLD<li>
    <li key="2016">NEW<li>
  </ul>
  ```

  ## 알고리즘
  Diffing 알고리즘은 Heuristics 알고리즘을 이용하여 순회하고, 변경사항을 업데이트한다.  
  하지만 Heuristics 알고리즘은 중요한 정보만 고려하여 최선의 값을 찾아내는 알고리즘이다.  
  이로 인해 100% 정확하지 않다는 공식 홈페이지의 안내가 존재한다.  

  ## 참고 자료
  - ### <a href="https://ko.legacy.reactjs.org/docs/reconciliation.html#gatsby-focus-wrapper">재조정 (Reconciliation)</a>
  - ### <a href="https://velog.io/@joy37/React-diffing-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98">React Diffing 알고리즘</a>
  - ### <a href="https://velog.io/@joy37/Heuristic-Algorithm%EC%9D%B4%EB%9E%80">Heuristic Algorithm이란?</a>