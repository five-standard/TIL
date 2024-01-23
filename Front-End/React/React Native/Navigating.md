# Navigating

> **React Native Navigating (feat. expo)**

React에서 네비게이팅을 하는 방법을 정리해두었다.  
 참고로 사용한 라이브러리는 React Navigation (6.x)이다.

## Stack Navigation

![](https://i.stack.imgur.com/FiniU.png)

흔히 아는 Stack 자료구조를 이용한 Navigation이다.  
웹의 방문 히스토리와 거희 같은 개념이다.

### 코드 형태

```js
const Stack = createNativeStackNavigator();

return (
  <NavigationContainer>
    <Stack.Navigator
      initialRouteName="First" // 첫 화면을 설정하는 옵션이다.
      screenOptions={{ headerShown: false }} // 기본 헤더를 숨기는 옵션이다.
    >
      <Stack.Screen name="First" component={First} />
      <Stack.Screen name="Second" component={Second} />
    </Stack.Navigator>
  </NavigationContainer>
);
```

## TabBar Navigation

![](https://miro.medium.com/v2/resize:fit:930/1*CnV48AaOC5HreH7KQN4nUw.png)
하단 바를 이용하여 이동하는 Navigation이다.  
흔히들 생각하는 그 네비게이션 바가 맞다.

### 코드 형태

```js
const Tab = createBottomTabNavigator();

<NavigationContainer>
  <Tab.Navigator
    initialRouteName="First" // 첫 화면을 설정하는 옵션이다.
    screenOptions={{ headerShown: false }} // 기본 헤더를 숨기는 옵션이다.
  >
    <Stack.Screen
      name="First"
      component={First}
      tabBarIcon={() => <TabIcons name="Heart" />} // 탭바의 아이콘을 설정하는 옵션이다.
    />
    <Stack.Screen name="Second" component={Second} />
  </Tab.Navigator>
</NavigationContainer>;
```

## Drawer Navigation

![](https://lh3.googleusercontent.com/W4QDMYeNtcm37g2JfKKj5lv8rJ6KGLb9vZdYUNEpjixpHDjjQ_hPrwnj5Ruo1ZYHyukHLRQCtXrzQV6gLzRSNE-w60QYjFcUZZ_2=w1064-v0)
아직 사용은 못해봤으나, 옆에서 나오는 네비게이션 바를 이용한 Navigation이다.  
 유튜브 웹의 오른쪽에 있는 네비게이션 바를 생각하면 편하다.
