# Usage

> **코드 두줄로 가볍게 사용하기**

```js
import { projectName } from "./store.module";

const Test = () => {
  const { state, setState } = projectName();

  return <div>{state}</div>;
};
```
