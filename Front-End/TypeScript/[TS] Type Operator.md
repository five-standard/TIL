# Type Operator

  ## Union Type
  유니온 타입이란, 자바스크립트의 OR 연산자와 같이 'A나 B이다' 라는 의미의 타입이다.  
  
  ```
  function logText(text: string | number) {
    // ...
  }
  ```

  해당 함수의 파라미터에는 문자열과 숫자 둘 다 올 수 있다.  
  이처럼 `|`연산자를 사용하여 타입을 여러 개 연결하는 방식을 유니온 타입 정의 방식이라고 한다.

  ### 유니온 타입의 장점
  유니온 타입을 사용하면 **여러 타입을 한 변수에 선언할 수 있다는 것**이 제일 큰 장점이다.  

  ```js
  // any를 사용하는 경우
  function getAge(age: any) {
    age.toFixe(); // 에러 발생, age의 타입이 any로 추론되기 때문에 숫자 관련된 API를 작성할 때 코드가 자동 완성되지 않는다.
    return age;
  }

  // 유니온 타입을 사용하는 경우
  function getAge(age: number | string) {
    if (typeof age === 'number') {
      age.toFixed(); // 정상 동작, age의 타입이 `number`로 추론되기 때문에 숫자 관련된 API를 쉽게 자동완성 할 수 있다.
    return age;
    }
    if (typeof age === 'string') {
      return age;
    }
    return new TypeError('age must be number or string');
  }
  ```
  또한 any를 사용하면 타입이 any가 되기 때문에 자동완성이 작동하지 않는다.  
  하지만 유니온 타입을 사용하면 **해당 타입들에서 사용 가능한 자동완성을 사용할 수 있다.**

  ### 주의할 점
  ```js
  interface Person {
    name: string;
    age: number;
  }
  interface Developer {
    name: string;
    skill: string;
  }
  function introduce(someone: Person | Developer) {
    someone.name; // O 정상 동작
    someone.age; // X 타입 오류
    someone.skill; // X 타입 오류
  }
  ```
  인터페이스를 이용하여 유니온 타입을 생성하는 경우, 타입스크립트는 함수 호출 시점에 어느 타입이 올지 알 수 없어 최대한 오류가 나지 않게 작동한다.  
  이로 인해, 함수 내부에서는 **타입 가드로 타입 범위를 좁히지 않는** 한, 두 타입에 공통적으로 존재하는 속성만 사용하게 된다

  ## Intersection Type
  인터섹션 타입은 여러 타입을 모두 만족하는 하나의 타입을 의미한다.

  ```js
  interface Person {
    name: string;
    age: number;
  }
  interface Developer {
    name: string;
    skill: number;
  }
  type Capt = Person & Developer;
  ```
  해당 코드는 **Person과 Developer의 타입 정의를 `&`연산자를 이용하여 합친 후, 한 타입에 할당**한 코드이다.

  아래와 같은 결과가 나온다
  ```js
  {
    name: string;
    age: number;
    skill: string;
  } //이해가 되지 않는다면, 교집합을 떠올려보면 된다.
  ```


