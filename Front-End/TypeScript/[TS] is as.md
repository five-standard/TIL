# is as
  > **애매한 타입들을 확실히 할 때 사용하는 키워드들**

  타입이 확실하지 않은 값들의 타입을 확실히 할 때 사용하는 키워드들이다.

  ## is
  함수의 return 값이 true 라면 함수가 호출된 범위 내에선 변수를 특정 타입으로 명시하라는 키워드이다.

  ```js
  function isString(test: any): test is string{ 
    return typeof test === "string";
    // return 값이 true라면 test는 string으로 명시된다.
  }

  function example(foo: any){
      if(isString(foo)){
          console.log("it is a string" + foo);
          console.log(foo.length); // string과 array에서만 작동하는 함수이다.
      }
  }
  
  example("hello world");
  ```

  ## as
  컴파일 단계에서 타입스크립트가 감지하지 못하는 애매한 타입 요소들을 직접 명시해주는 키워드이다.

  ```js
    const myCanvas1 = document.getElementById("main_canvas");
    // 타입스크립트는 해당 코드가 HTMLElement를 가질 것이란 사실만 알 수 있다.

    const myCanvas2 = document.getElementById("main_canvas") as HTMLCanvasElement;
    // 타입스크립트는 해당 코드가 HTMLCanvasElement를 가질 것이라고 확실히 알 수 있게 됬다.
    
    const myCanvas3 = <HTMLCanvasElement>document.getElementById("main_canvas");
    // 이런 방식으로 작성할 수도 있다. 다만 코드가 tsx 파일 내에 있어야 한다.
  ```