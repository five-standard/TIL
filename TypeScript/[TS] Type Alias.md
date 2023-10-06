# Type Alias
  > **타입식 대명사**

  특정 타입이나 인터페이스를 참조할 수 있는 타입 변수이다.
  보통 중복된 타입 코드를 줄이고, 주요 데이터 타입이나 인터섹션 타입, 유니언 타입 등의 정의에 사용된다.
  
  ## 사용
  한 개의 변수에만 지정하는 경우에는 아래와 같이 사용할 수 있다.
  ```js
  type Types = string;
  const Str: Types = "String";
  // (const str: string = "string")과 같다
  ```
  이외에도 객체 형식으로 생성하여 interface같이 사용할 수도 있다.
  ```js
  type Types = {
    str: string | number;
    int: number;
    bol: boolean;
  }

  const Obj: Types = {
    str: "String",
    int: "Integer",
    bol: "Boolean"
  }

  const Func: Types = (str, int, bol) => {
    return `string = "${str}", number = ${int}, boolean = ${bol}`;
  }
  ```

  ## 특이한 타입들
  위에서도 나와있지만, Type Alias는 데이터 타입, 인터섹션 타입 등의 정의에 사용된다.  
  그로 인해 아래와 같은 타입들을 지원한다.
  ```js
  type Intersection = Type1 & Type2; // 인터섹션

  type Union = Type1 | Type2 // 유니언

  type Utility = { Data1: string; Data2: number; Data3: boolean; } // 유틸리티

  type Mapped = { [I in Items]: number } // 맵드

  // 참고로 인터페이스는 해당 타입들을 지원하지 않는다.
  ```

  ## Interface와의 차이점
  - ### 원시 타입을 정의할 수 있다.
    Interface는 객체에서만 쓸 수 있기 떄문에, 원시 타입을 정의할 수 없다.  
    반면에 Type Alias는 원시 타입을 정의할 수 있다.

  - ### 같은 이름의 타입을 선언할 수 없다.
    Interface는 같은 이름의 Interface를 여러개 생성할 수 있으며, 자동으로 병합된다.  
    하지만 Type Alias는 같은 이름의 Alias를 여러 번 생성할 수 없다.

  - ### 확장이 불가능하다.
    Interface는 extends를 통해 확장이 가능하지만, Type Alias는 그렇지 않다.  
    다만 &을 사용하여 인터섹션을 생성하는 것은 가능하다.