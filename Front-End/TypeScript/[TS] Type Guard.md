# Type Guard
  > **Typescript에서 타입을 좁혀나간는 데 도웅믈 주는 것들**
  
  Type Guard를 사용하면 조건문에서 객체의 타입을 좁혀나갈 수 있다.


  ## typeof
  JavaScript에서 이미 존재하는 연산자로, 피연산자의 타입을 판단하여 문자열로 반환해준다.
  
  ```js
  const testFunc = (arg: string | number) => {
    arg.substring(3); // ts(2339) : Property 'substring' does not exist on type 'string | number'.
    // arg가 string일 수도, number일 수도 있기 때문에 오류가 발생한다.

    if (typeof arg === "string") {
      // 아래의 arg는 무조건 string 타입으로 인식된다.
      arg.substring(3);
    }
  }
  ```

  ## instanceof
  instanceof는 TypeScript에서 생긴 연산자로, 판별할 객체가 특정 클래스에 속하는 지 확인할 수 있다.

  ```js
  class Student {
    name: string;
    age: number;
  }
  class School {
    location: string;
  }

  function testFunc(arg: Student | School) {
    if (arg instanceof Student) { // arg가 Student 클래스에 포함됬을 때
      console.log(arg.name);
      console.log(arg.location); // ts(2339) : Property 'location' does not exist on type 'Student'.
    } else { // arg가 School 클래스에 포함됬을 때
      console.log(arg.location);
      console.log(arg.name) // ts(2339) : Property 'name' does not exist on type 'School'.
    }
  }
  const student = new Student();
  testFunc(student);
  ```

  ## Custom Type Guard
  개발자가 직접 타입 가드를 정의할 수도 있다.

  ```js
  interface Animal {
    name: string;
    age: number;
  }

  interface Flower {
    type: string;
    age: number;
  }

  interface ExampleInfo {
    page: number;
    infoBody: Animal | Flower;
  }

  // Custom Type Guard
  function isAnimal(arg: any): arg is Animal {
    return arg.name !== undefined;
  } // arg의 타입이 animal인지 아닌지를 반환한다.

  function doSomething(arg: ExampleInfo) {
    const { page, infoBody } = arg;

    if (isAnimal(infoBody)) { // 무조건 animal일 떄만 작동한다.
      console.log(infoBody.name);
    } else { // 이외에는 animal이 아닐 때만 작동한다
      console.log(infoBody.type);
      console.log(infoBody.name); // error
    }
  }

  const puppy: Animal = {
    name: "puppy",
    age: 5,
  };
  const animalInfo: ExampleInfo = {
    page: 10,
    infoBody: puppy,
  };
  doSomething(animalInfo);
  ```