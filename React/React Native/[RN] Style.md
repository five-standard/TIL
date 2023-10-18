# Style
  > **React Native의 스타일링**
  
  React Native는 styled-component가 아닌 객체로 스타일을 적용한다.  
  해당 객체의 값을 컴포넌트의 style 속성의 값으로 사용하여 스타일을 적용할 수 있다.

  ```js
  const styles = {
    container: {
      flex: 1,
      backgroundColor: '#fff',
    }
  }
  ```

  ## Inline
  참고로 style 속성의 값을 이용하여 스타일링하기 떄문에, 인라인으로도 스타일링이 가능하다.
  ```js
  <View style={
    flex: 1,
    backgroundColor: '#fff'
  } />
  ```

  ## StyleSheet
  앞서 말했듯이, React Native는 객체를 통해 스타일을 적용하는데, 해당 객체에 자동 완성 기능을 추가하기 위해 사용한다.
  ```js
  const styles = StyleSheet.Create({
    container: {
      flex: 1,
      backgroundColor: '#fff',
    }
  })
  ```