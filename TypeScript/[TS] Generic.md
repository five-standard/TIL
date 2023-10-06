# Generic
  제너릭 타입은 타입에 유연성을 제공하여 컴포넌트 등에서 재사용을 가능하게 해주는 타입이다.
  여기서 타입의 유연성은 **:string, :number와 같은 고정 타입**이 아닌 사용에 따라 여러 타입을 사용하게 해준다는 의미이다.

  ## 사용 이유
  any에 존재하지 않는 타입 검사를 사용하여 입력값과 출력값의 타입이 동일한지 검증하기 위해서이다.

  더 정확히 알기 위해, 아래에 예시를 적어두었다.
  ```js
    //any를 사용한 코드
    function Hello(data: any) : any {
      return data;
    }

    const World2 = Hello(1);
    World2.split(' ') // 실행시 오류가 발생하지만, ESLint가 감지하지 못했다.

    //제네릭을 사용한 코드
    function Hello<T>(data: T) : T {
      return data;
    }

    const World2 = Hello(1);
    World2.split(' ') // 실행시 오류가 발생하며, ESLint가 감지하여 밑줄을 출력한다.
  ```

  ## 제네릭 선언
  ```js
    function logText<T>(text: T): T {
      return text;
    }
  ```
  제네릭은 기본적으로 T를 이용하여 선언한다.  
  **(참고로 이 T는 다른것으로 바꿀 수 있는데, T가 들어간 부분을 전부 같은 이름으로 바꾸면 된다)**

  ## 제네릭 확장
  ```js
    interface Text {
      Numb: number;
    }

    function logText<T extends Text>(text: T): T {
      console.log(text.length);
      let Numb = 0;
      return [text, Numb];
    }
  ```
  제네릭도 extends를 이용하여 확장이 가능하다.  
  다만 `<T>`안에 붙여야 한다.

  ## 제네릭 인터페이스 / 클래스
  ```js
    interface GenericLogTextFn {
      <T>(text: T): T;
    }

    class GenericMath<T> {
      pi: T;
      sum: (x: T, y: T) => T;
    }
  ```
  제네릭의 변형 방식<b>(`let str: <T>(textL T) => T = logText`)</b>을 응용하여 제네릭 인터페이스와 클래스를 생성할 수 있다.

  여기서 인터페이스와 클래스의 선언 방식이 약간 다르다.  
  **클래스는 이름 오른쪽에 `<T>`를 무조건 붙여야 한다.**

  ## 제네릭 타입 제약
  ```js
    function Hello<T>(data: T) : T {
      return data.length;
    }
  ```
  인자의 타입에 선언된 T는 아직 어떤 타입인제 구체적으로 정의하지 않았기 때문에 오류가 발생한다.  
  하지만 **배열 타입을 정의하지 않고, length 속성만은 허용**하려면 **interface**를 사용해야 한다.

  ```js
    interface LengthWise {
      length: number;
    }

    function logText<T extends LengthWise>(text: T): T {
      console.log(text.length);
      return text;
    }

    // 배열 타입을 직접 선언
    //function logText<T>(text: T[]): T[] {
    //  console.log(text.length);
    //  return text;
    //}

  ```

  위에 적혀있던 **제네릭 확장**을 응용하여 length를 설정할 수 있다.  
  다만 **length에 대해 동작하는 인자**만 넘겨받을 수 있다. (배열, 문자열)
