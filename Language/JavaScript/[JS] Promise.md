# Promise
  > **비동기 처리를 도와주는 객체**
  
  JS에서 비동기 작업의 최종 완료, 혹은 실패를 나타내는 독자적인 객체이다.  
  결과 대기가 아닌 결과 제공 약속을 반환한다는 의미로 "Promise"라 명명됬다고 한다.

  ## 상태
  - ### 대기
    이행하지도, 거부하지도 않은 초기 상태.

  - ### 이행
    비동기 처리가 성공적으로 이행된 상태.

  - ### 거부
    비동기 처리가 거부된 상태.

  대기중인 프로미스는 값과 함께 이행되거나 오류로 인해 거부될 수 있다.
  프로미스가 이행되거나 거부되면 then 메서드를 통해 함수들이 호출된다.

  ## 생성
  ```js
  const myPromise = new Promise((resolve, reject) => {
    const data = axios.get("URL");
    
    if(data) {
      resolve(data); // 함수가 정상적으로 실행됬을 때
    } {
      reject("Error"); // 함수에 오류가 발생했을 때
    }
  })
  ```

  ## then, catch
  프로미스의 반환값을 받거나(then) 오류를 받는(catch)함수들이다.
  ```js
  myPromise
   .then(res => {
    console.log(res);
   })
   .catch(err => {
    console.log(err);
   })
  ```

  ## Promise Chaning
  프로미스가 이행된 후 실행될 콜백 함수에 또 프로미스 함수를 넣는 것을 말한다.
  프로미스 이행 이후의 then 함수들은 전부 프로미스로 묶여있기 때문에 따로 비동기 처리를 해 줄 필요 없다.

  ```js
  myPromise
   .then(myPromise) // 여기부터 체인된다.
   .then(myPromise) // 참고로 체인된 프로미스에 다시 체인할 필요 없다.
   .then(myPromise) // .then(myPromise.then(myPromise.then(myPromise)))는 좀 아니지 않은가?
   .then(myPromise)
   .then(myPromise)
   .catch(err => {
    console.log(err);
   })
  ```

  ## Async, Await
  ### Async
  프로미스 함수를 간단히 만들 수 있게 도와주는 기능이다.
  new Promise를 사용하지 않아도 function 앞에 붙이면 프로미스 값이 반환된다.
  ```js
  async function myPromise() {
    const data = await axios.get("URL"); // await는 아래에 설명되어 있다.
    return data; // 자동으로 프로미스 값이 반환된다.
  }

  myPromise.then(res => {
    console.log(res.data);
  });
  ```

  ### Await
  특정 함수가 끝날 때까지 다음 코드가 동작하지 않게 해주는 기능이다.
  동기 함수, 비동기 함수 상관없이 앞에 붙일 수 있으며, async 함수 안에서만 쓸 수 있다.

  ```js
  async function myPromis() {
    const data = await axios.get("URL"); // 이 코드가 끌날 때까지 data는 반환되지 않는다.
    return data;
  }

  myPromise.then(res => {
    console.log(res.data);
  });
  ```
  