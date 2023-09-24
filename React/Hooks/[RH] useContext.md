# useContext
  > **Context를 더 편하게 사용할 수 있게 해주는 훅**

  Context를 더 편하게 사용할 수 있게 해주는 훅이다.  
  여기서 Context란 Props를 일일히 넘길 필요 없이, 하위 컴포넌트들에 데이터를 제공하게 해주는 기능을 의미한다.

  ## 사용 이유
  중간에 코드가 바뀌면 일일히 다 찾아 바꿔야 하며, 해당 데이터가 필요하지 않은 컴포넌트에도 데이터가 전달되어 코드가 지저분해지기도 하는데, 이를 해결하기 위해 useContext를 사용한다.

  ## 사용
  ```js
  [App.js]
    export const AppContext = createContext();
    
    export const App = () => {
      const user = {
        name: "김채원",
        job: "가수"
      };

      return <>
        <AppContext.Provider value={user}>
          <div>
            <Children />
          </div>
        </AppContext.Provider>
      </>
    }
  
  [Children.js]
    import { AppContext } from './App';

    export const Children = () => {
      const user = useContext(AppContext);

      return <>
        <h3>{user.name}</h3>
        <h3>{user.job}</h3>
      </>
    }
  ```