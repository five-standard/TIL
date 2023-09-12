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
   
