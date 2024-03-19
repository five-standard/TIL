# Execution Context

> **코드가 실행되는 범위를 나타내는 추상적인 개념**

코드가 실행되는 범위를 나타내는 추상적인 개념이다.  
만약 코드가 실행된다면 실행 컨텍스트 내에서 실행된다.

참고로 엔진이 코드를 실행하기 위해선 아래와 같은 정보들이 필요하다.

- 변수: 전역/지역/매개변수, 객체의 프로퍼티
- 함수 선언
- 변수의 유효범위
- this

## Execution Stack

호출 스택(콜 스택)과 같은 말로, 코드가 실행되며 만들어지는 실행 컨택스트들이 저장된다.

## Execution Context의 순서

- ### Creation Phase

  - **LexicalEnvironment 컴포넌트 생성**  
    Lexical Environment는 변수와 변수에 대입된 값이 매핑되는 컴포넌트이다.  
    함수나 변수의 이름과 같은 구분자인 identifier를 이용해 식별자를 찾고, 값을 매핑한다.  
    정확히는, 아래와 같은 일들을 한다

    - **Environment Records**  
      Lexical Environment 내부에 함수와 변수를 기록한다.

    - **Reference to the outer Environment**  
      해당 Lexical Environment에서 변수를 못 찾았을 때 외부 환경에서 변수를 찾아 본다는 의미이다.
    - **This Binding**  
      this의 값을 결정한다.  
      Object Reference로 호출됬다면 해당 객체를 가리키며,
      그 외에는 window를 가리키거나 undefined를 가리킨다 (strict mode에서)

  - **VariableEnvironment 컴포넌트 생성**  
    Lexical Environment와 동일하나, var만 저장한다는 차이점이 있는 컴포넌트이다.

  > **📕 정리**  
  > Scope Chain, 변수, 함수, 인자를 만든다.  
  > this를 결정한다.  
  > Syntax Parser가 코드를 읽으며 기계어로 변환한다.  
  > 코드를 읽으며 변수와 함수의 선언을 찾고, 메모리에 해당 변수와 함수를 기록한다. (호이스팅)

- ### Execution Phase
  엔진이 코드를 읽으며 실행하는 단계이다.  
  이 단계에서 선언했던 변수들에 값이 할당된다.

## 실행 예시

![](https://velog.velcdn.com/post-images%2Fimacoolgirlyo%2Fc4abfd80-427a-11e9-b77a-574f9b588be3%2F-2019-03-09-11.50.23.png)

1. 엔진이 스크립트를 만나 전역 컨텍스트를 만든다.
   이 때 a b multiply는 LexicalEnvironment에서, c는 VariableEnvironme에서 매핑된다.

2. Execution Phase에서 코드가 실행되고 변수에 값이 할당된다.

![](https://velog.velcdn.com/post-images%2Fimacoolgirlyo%2Fc7e15ef0-427a-11e9-b77a-574f9b588be3%2F-2019-03-09-11.50.32.png)

3. multiply 함수가 호출되며 multiply 함수의 컨텍스트가 생성된다.

![](https://velog.velcdn.com/post-images%2Fimacoolgirlyo%2Fce2b2c50-427a-11e9-b77a-574f9b588be3%2F-2019-03-09-11.50.48.png)

4. 함수가 값을 리턴하며 호출 스택에서 제거되고, c의 값이 업데이트된다.

5. 프로그램이 종료된다.

## 참고

let과 const는 실행시 어떤 값도 가지고 있지 않지만 var는 undefined를 가지고 있다.

이는 실행 컨텍스트가 생성되는 동안, 함수는 environment에 전부 저장되지만 변수들은 기본값으로 undefined를 가지기 떄문이다.

이로 인해 let과 const는 reference error가 발생하지만 var는 undefined가 반환되는 것이다.
