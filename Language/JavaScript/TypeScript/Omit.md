# Omit

> **타입에서 특정 속성만 제거해서 가져오기**
> 어떠한 인터페이스/타입에서 특정 속성만 제거해서 가져올 수 있게 해주는 유틸리티 타입이다.

## 사용법

```ts
interface test {
  type1: string;
  type2: string;
  type3: string;
}

interface test2 extends Omit<test, "type1"> {
  // 인터페이스 확장에도 유용하게 사용 가능
  type1: number;
  type2: string;
  type3: string;
}

const data: Omit<test, "type1"> = {
  type2: "hello",
  type3: "world",
};

const data: Omit<test, "type1" | "type2"> = {
  // 여러개를 제거시 유니언 타입 사용
  type3: "world",
};
```
