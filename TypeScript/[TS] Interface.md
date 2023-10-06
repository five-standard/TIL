# Interface
  Interface란 자주 사용하는 타입들을 **object 형태의 묶음**으로 정의해 새로운 타입을 만드는 기능이다.

  ## 선언
  ```js
  interface User {
    name: string;
    age: number;
  }
  ```

  ## 활용
  활용시 변수, 함수, 클래스 등은 인터페이스의 형태를 준수해야 한다.  

  ### 변수의 타입
  ```js
  interface User {
    name: string;
    age: number;
  }

  const Gijun: User = { 
    name: "Gijun", 
    age: 17
  }
  ```

  ### 함수의 타입
  ```js
  interface SquareFunc {
    (num: number): number;
  }
  const squareFunc: SquareFunc = function (num: number) {
    //num은 반환값으로, Props에 무조건 포함되야 한다
    return num * num;
  }
  console.log(squareFunc(10)); // 100
  ```
  
  ### 클래스의 타입 (프로퍼티)
  ```js
  interface ITodo {
    id: number;
    content: string;
    completed: boolean;
  }
  class Todo implements ITodo {
    constructor (
      public id: number,
      public content: string,
      public completed: boolean
    ) { }
  }
  const todo = new Todo(1, 'Typescript', false);
  console.log(todo);
  ```
  
  ### 클래스의 타입 (프로퍼티와 메소드)
  ```js
  interface IPerson {
    name: string;
    sayHello(): void;
  }
  class Person implements IPerson {
    constructor(public name: string) {}
    sayHello() {
      console.log(`Hello ${this.name}`);
    }
  }
  function greeter(person: IPerson): void {
    person.sayHello();
  }
  const me = new Person('Lee');
  greeter(me); // Hello Lee
  ```
  
  ## 상속
  interface는 **extends**를 사용하여 다른 interface를 상속받을 수 있다. 
  ```js
   interface Person {
     name: string;
     age: number;
   }
   interface Developer extends Person {
     position: string;
   }
   const jinyoung: Developer = {
     name: "jinyoung",
     age: 24,
     position: "FE"
   };
  ```
  
  물론 복수의 인터페이스도 상속받을 수 있다.
  ```js
  interface Person {
    name: string;
    age: number;
  }
  interface Developer {
    name: string;
    age: number;
    position: string
  }
  interface DevOps extends Person, Developer {
     devOps: boolean
  }
  const hyunsu: DevOps = {
    name: "hyunsu",
    age: 24,
    position: "BE",
    devOps: true
  };
  ```

  ## 선택적 프로퍼티
  만약 프로퍼티가 선택적으로 쓰이는 경우, **프로퍼티의 이름 뒤에 ?를 붙여 선택적프로퍼티로** 만들 수 있다.
  ```js
  interface UserInfo {
    username: string;
    password: string;
    age?    : number;
    address?: string;
  }
  const userInfo: UserInfo = {
    username: 'ungmo2@gmail.com',
    password: '123456'
  }
  console.log(userInfo);
  ```

  ## 덕 타이핑
  인터페이스를 구현하는 방법으로 타입 체크를 통과하는 것만 있는 것은 아니다.  
  타입스크립트는 **특정 인터페이스에서 정의한 프로퍼티나 메소드를 가지고 있다면, 그인터페이스를 구현한 것으로 인정**한다.  
  이를 **덕 타이핑**이라고 한다.
  ```js
  interface IDuck { // 1
    quack(): void;
  }
  class MallardDuck implements IDuck {
    quack() {
      console.log('Quack!');
    }
  }
  class RedheadDuck { // 2
    quack() {
      console.log('q~uack!');
    }
  }
  function makeNoise(duck: IDuck): void {
    duck.quack();
  }
  makeNoise(new MallardDuck()); // Quack!
  makeNoise(new RedheadDuck()); // q~uack!
  ```
