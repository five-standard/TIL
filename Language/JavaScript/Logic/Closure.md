# Closure

> **내부 함수에서 외부 함수의 범위에 대한 접근을 제공하는 것**

Javascript에서 함수가 생성될 떄마다 생성되는 것으로, 외부 함수/값의 범위에 대한 접근을 제한한다.

## 어휘적 범위 지정 (Lexical Scoping)

```js
var data = "Text2";

function init() {
  var data = "Text";
  function log() {
    console.log(data);
  }
  log(); //Text
  log2(); //Text2;
}

function log2() {
  console.log(data);
}

init();
```

함수가 호출된 시점에 따라 상위 스코프를 결정하는, 동적 스코핑과 반대되는 개념이다.

## let과 const의 범위 지정

[Scope.md 파일](https://github.com/six-standard/TIL/blob/main/Language/JavaScript/Logic/Scope.md)을 보면 확인할 수 있다.
