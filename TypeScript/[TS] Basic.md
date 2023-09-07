# Basic
  ## 기본 타입 선언
   - **문자열** - `const hello: string = "helloWorld!";`

   - **숫자** - `let tripleSeven: number = 777;`
   - **배열** -  
   `let arr1: number[] = [10, 20, 30];`  
   `let arr2: Array<number> = [10 , 20, 30];`  
   `let arr3: Array<string> = ["hello", "world"];`  
   `let arr4: [string, number] = ["jinyoung", 24]; //각 항목마다 타입을 줄 경우`
   - **객체** - `let jinyoung: object = { name: "jinyoung", age: 24 };` 
   - **불리언** - `let isThatTrue: boolean = true;`
  
  ## 함수 선언
   - **함수 타입 선언**
   ``` 
    function add(x: number, y: number //매개변수): number //return 값 {
      return x + y;
    }
   ```

   - **선택적 매개변수**  
   변수 이름 뒤에 <b>?</b>를 붙여주면 된다.
   ```
    function buildName(firstName: string, lastName?: string) {
      if (lastName)
        return firstName + " " + lastName;
      else
        return firstName;
    }

    let result1 = buildName("Bob"); //Bob
    let result2 = buildName("Bob", "Adams", "Sr."); //Compile Error
    let result3 = buildName("Bob", "Adams"); //Bob Adams
   ```

  ## Interface
   Interface란 자주 사용하는 타입들을 **object 형태의 묶음**으로 정의해 새로운 타입을 만드는 기능이다.

   - **선언**
   ```
    interface User {
      age: number;
      name: string;
    }
   ```

  - **변수 활용** - `const jinyoung: User = { name: "jinyoung", age: 24 }`

   - **확장**
   ```
    interface Person {
      name: string;
      age: number;
    }

    interface Developer extends Person {
      position: string;
    } //똑같은 값들을 칠 필요 없이 특정 값이 추가된 interface를 만들 수 있다.

    const jinyoung: Developer = {
      name: "jinyoung",
      age: 24,
      position: "FE"
    };
   ```
   
