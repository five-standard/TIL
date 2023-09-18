# 배열 반복문들
  > **배열에서 주로 쓰이는 반복문들**

  배열에서 주로 쓰이는 반복문들을 정리해두었다.  
  참고로 모든 반복문들은 순서대로 <b>[현재 요소, 인덱스, 배열]</b>을 매개변수로 넣을 수 있다. 

  ## ForEach
  ForEach는 단순히 각 배열 요소마다 특정 함수를 실행하는 함수이다.

  ```js
  const myArr = [1, 2, 3, 4, 5];

  myArr.forEach((currentElement, index, array) => { 
    console.log(currentElement); // 1, (2, 3, 4, 5)
    console.log(index); // 0, (1, 2, 3, 4)
    console.log(array); // [1, 2, 3, 4, 5]
  });
  ```

  ## Filter
  Filter는 배열의 일부를 <b>'얕은 복사'</b>로 복사하고, 특정 함수의 리턴값에 부합하는 요소만 <b>반환(필터링)</b>하는 함수이다.

  참고로 <b>얕은 복사</b>이기 때문에 반환된 값이 담긴 변수를 수정해도, 원래 값엔 영향이 가지 않는다.

  ```js
  const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
  const result = words.filter((word) => word.length > 6); //6글자 이상인 값만 반환한다.
  console.log(result); // ["exuberant", "destruction", "present"]
  ```

  ## Map
  Map은 각 배열 요소마다 특정 함수를 실행하여 나온 반환값을 모아 새로운 배열을 생성하는 함수이다.

  ```js
  var numbers = [1, 4, 9];
  var doubles = numbers.map(function (num) {
    return num * 2;
  });
  // doubles는 [2, 8, 18]
  // numbers는 [1, 4, 9]
  ```
