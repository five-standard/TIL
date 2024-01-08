# Tags
  > **React Native의 태그**

  React Native에선 HTML 태그를 제외한 새로운 태그가 존재한다.  
  해당 태그들을 사용하기 위해선 React-Native에서 import해와야 한다.  
  ``import { View, Text, Image } from "react-native"``

  ## View
  div와 비슷한 컨테이너 태그이다.  
  다만 div처럼 바로 텍스트를 넣을 수는 없으며, ``<Text>``를 사용해야 한다.  
  참고로 기본적으로 **FlexBox 속성**을 부여받는다.
  ```js
  <View style={style.Container}>
    <Text>Hello World!</Text>
  </View>
  ```

  ## Text
  React Native에서 Text를 출력하는데 쓰이는 태그이다.
  ```js
  <Text style={style.Text}>Hello World!</Text>
  ```

  ## Image
  React Native에서 Image를 출력하는데 쓰이는 태그이다.
  ```js
  <Image source={{uri: "/Path/image/Hi.png"}} />
  ```

  ## TextInput
  React Native에서 입력을 받는데 쓰이는 태그이다.  
  input의 속성 일부(onChangeText, value)와 Native 전용 속성 일부(onPress)를 가지고 있다.
  ```js
  <TextInput
    style={style.Input}
    value={value}
    onChangeText={handleChange}
  />
  ```

  ## ScrollView
  React Native에서 스크롤을 생성해주는 태그이다.
  기본적으로 React Native에선 스크롤을 자동 생성해주지 않는데, 이를 보완하기 위해 사용한다.
  ```js
  <ScrollView style={style.ScrollView} />
  ```

  ## StatusBar
  스마트폰의 상단 바를 수정할 수 있게 해주는 태그이다.
  ![](https://velog.velcdn.com/images/ttoottie/post/d957b86c-3bcd-49b9-b670-1f6d20c60bf9/image.png)
  ```js
  <StatusBar barStyle="light-content" />
  ```

  ## Button
  React Native에서 버튼을 생상하는데 쓰이는 태그이다.  
  onClick대신 onPress를 사용한다는 점만 제외하면, 일반 Button태그와 비슷하다.
  ```
  <Buton onPress={handlePress} style={style.button} />
  ```
  
  