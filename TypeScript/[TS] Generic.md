# Generic
  제너릭 타입은 타입에 유연성을 제공하여 컴포넌트 등에서 재사용을 가능하게 해주는 타입이다.  
  여기서 타입의 유연성은 **정적 타입이 아닌 동적 타입**을 사용할 수 있게 해준다는 의미이다.

  ## 사용 이유
  any에 존재하지 않는 타입 검사를 사용하여 입력값과 출력값의 타입이 동일한지 검증하기 위해서이다.
  ```js
  //any
  function Hello(data: any) : any { return data; }
  const World2 = Hello(1);
  World2.split(' ') // ESLint에서 감지되지 않는 오류가 발생한다.
  
  //Generic
  function Hello<T>(data: T) : T { return data; }
  const World2 = Hello(1);
  World2.split(' ') // ESLint에서 감지되는 오류가 발생한다.
  ```

  ## 제네릭 선언
  제네릭은 기본적으로 <T>를 이용하여 선언한다.  
  **(참고로 이 T는 다른것으로 바꿀 수 있는데, T를 전부 같은 이름으로 바꾸면 된다)**
  ```js
  function logText<T>(text: T): T {
    return text;
  }
  ```

  ## 제네릭 확장
  제네릭도 extends를 이용하여 확장이 가능하다.
  ```js
  interface Text { Int: number; }

  function logText<T extends Text>(text: T): T {
    let Int = 0;
    console.log(text);
    return [text, Int];
  }
  ```

  ## 제네릭 인터페이스 / 클래스
  제네릭의 변형 방식<b>(`let str: <T>(textL T) => T = logText`)</b>을 응용하여 제네릭 인터페이스와 클래스를 생성할 수 있다.  
  **참고로 클래스 정의 시에는, 클래스 이름 끝에 <T>를 붙어야 한다**
  ```js
  interface GenericLogTextFn {
    <T>(text: T): T;
  }

  class GenericMath<T> {
    pi: T;
    sum: (x: T, y: T) => T;
  }
  ```

  ## 제네릭 타입 제약
  해당 제너릭 타입은 어떤 타입인지 구체적으로 정의하지 않았기 때문에, 배열 길이 확인 등의 함수에서 오류가 발생한다.  
  이럴 떄, **interface**를 사용하여 해당 함수들의 리턴값을 미리 정의해주면 해결할 수 있다.
  ```js
  function Hello<T>(data: T) : T {
    return data.length;
  }
  ```

  위에 적혀있던 **제네릭 확장**을 응용하여 함수의 리턴값을 정의할 수 있다.  
  (대신 해당 Props에는 해당 함수에 대응하는 값을 넘겨줘야 한다)
  ```js
  interface LengthWise { length: number; }

  function logText<T extends LengthWise>(text: T): T {
    console.log(text.length);
    return text;
  }
  ```