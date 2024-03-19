# Call Stack

> **함수의 위치를 추적하는 인터프리터를 위한 매커니즘**

Memory Heap, Callback Queue와 함꼐 JS 엔진을 구성하는 요소 중 하나로, 여러 함수를 호출하는 스크립트에서 해당 위치를 추적하는 인터프리터를 위한 매커니즘이다.

## 매커니즘

```js
function greeting() {
  // [1] 일부 코드가 들어갑니다.
  sayHi();
  // [2] 일부 코드가 들어갑니다.
}
function sayHi() {
  return "Hi!";
}

// `greeting` 함수를 호출합니다.
greeting();

// [3] 일부 코드가 들어갑니다.
```

1. greeting 함수가 리스트에 들어간다.
2. sayHi 함수가 리스트에 들어간다.
3. sayHi함수가 실행된 후, 콜스택에서 제거된다.
4. greeting 함수가 실행된 후, 콜스택에서 제거된다.
5. 코드가 종료된다.
