# FormData
  > **서버로 데이터를 보낼 때 사용하는 함수**

  ajax, axios 등으로 폼 전송을 가능하게 해주는 객체 형식의 데이터이다.  
  보통은 JSON을 이용하여 Key-Value 구조로 값을 보내지만, 이미지나 파일 등을 보내는 경우에 사용한다.

  ## 생성
  ``const (name) = new formdata();``
  
  ## 값 추가
  ``(name).append("key", value);``

  ## 값 존재 여부 확인
  ``(name).has("key")`` (boolean 타입의 값 반환)  
  ``(name).get("key")`` (값의 첫 값 반환)  
  ``(name).getAll("key")`` (모든 값을 배열 타입으로 반환)

  ## 값 순회
  ``(name).keys()`` (key값을 순회)  
  ``(name).values()`` (value값을 순회)  
  ``(name).entries`` (key와 value값을 동시에 순회, 객체를 순회하는데도 쓰인다)  

  참고로 formdata는 일반적인 방식으로 값을 출력할 수 없다.  
  위와 같은 순회 코드를 사용하여 값을 출력해야 한다.