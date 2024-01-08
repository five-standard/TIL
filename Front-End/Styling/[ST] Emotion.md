# Emotion

> **프레임워크에 구애받지 않고 쓸 수 있는 CSS in JS 라이브러리**

프레임워크에 상관없이 쓸 수 있는 CSS in JS 라이브러리이다.  
 emotion/css, emotion/styled, emotion/react 등을 지원한다.

## @emotion/react

emotion의 대표적인 패키지로, React의 스타일링을 지원한다.  
 제대로 사용하기 위해서는 Babel과 코드 내부에 [일부 세팅](https://emotion.sh/docs/css-prop)을 해줘야 한다

### 코드

```js
/** @jsx jsx */
import { jsx, css, Global, ClassNames } from "@emotion/react";

render(
  <div css={{ color: "hotpink" }}>
    <div
      css={css`
        color: green;
      `}
    />
    <Global
      styles={{
        body: {
          margin: 0,
          padding: 0,
        },
      }}
    />
    <ClassNames>
      {({ css, cx }) => (
        <div
          className={cx(
            "some-class",
            css`
              color: yellow;
            `
          )}
        />
      )}
    </ClassNames>
  </div>
);
```

## @emotion/styled

@emotion/react의 확장 패키지이다.  
 Emotion에 styled 함수를 추가해준다.

### 코드

```js
import styled from "@emotion/styled";

let SomeComp = styled.div({
  color: "hotpink",
});

let AnotherComp = styled.div`
  color: ${(props) => props.color};
`;

render(
  <SomeComp>
    <AnotherComp color="green" />
  </SomeComp>
);
```

## @emotion/css

Emotion의 여러 기능들을 이용할 수 있게 해주는 패키지이다.

### css

스타일링에 쓰이는 함수로, String Style과 Object Style등을 지원한다.

```js
// @live
import { css } from "@emotion/css";

const color = "darkgreen";

return (
  <div
    className={css`
      background-color: hotpink;
      &:hover {
        color: ${color};
      }
    `}
  >
    This has a hotpink background.
  </div>
);
```

### cx

여러 css 객체를 합쳐 한 객체로 만드는 것을 도와주는 함수이다.

```js
const cls1 = css`
  font-size: 20px;
  background: green;
`;
const cls2 = css`
  font-size: 20px;
  background: blue;
`;

const foo = true;
const bar = false;

return <div className={cx({ [cls1]: foo }, { [cls2]: bar })} />;
```

### injectGlobal

글로벌 스타일을 생성할 할 때 사용할 수 있는 함수이다

```js
import { injectGlobal } from "@emotion/css";

injectGlobal`
  * {
    box-sizing: border-box;
  }
  @font-face {
    font-family: 'Patrick Hand SC';
    font-style: normal;
    font-weight: 400;
    src: local('Patrick Hand SC'),
      local('PatrickHandSC-Regular'),
      url(https://fonts.gstatic.com/s/patrickhandsc/v4/OYFWCgfCR-7uHIovjUZXsZ71Uis0Qeb9Gqo8IZV7ckE.woff2)
        format('woff2');
    unicode-range: U+0100-024f, U+1-1eff,
      U+20a0-20ab, U+20ad-20cf, U+2c60-2c7f,
      U+A720-A7FF;
  }
`;
```

## JSX pragma

```js
/** @jsx jsx */ // React v16 이전
/** @jsxImportSource @emotion/react */ // React v16 이후
```

React의 내장 jsx 함수 대신 Emotion의 jsx함수를 쓰게 해주는 pragma이다.  
 CSS Props를 사용할 때 기능 테스트를 하거나 Babel 구성이 불가능할 때 사용한다.
