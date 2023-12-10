# CreateSlice
  > **createReducer + createAction**
  
  createReducer와 createAction의 역할을 함께 하는 함수이다.
  action을 위해 추가적인 js파일을 만들 필요가 없다는 장점이 존재한다.

  ```js
  // data.js
  import { createSlice } from '@reduxjs/toolkit';

  export const dataSlice = createSlice({
      name: "data",
      initialState: { value: "data" },
      reducers: {
          update: (state, action) => {
              state.value = action.payload
          },
      },
  });

  export default dataSlice.reducer;
  ```