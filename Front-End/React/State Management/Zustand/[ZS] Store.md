# Store

> **Redux보다 쉬운 Store**

```js
// store.module.ts

// js로 사용할 때.
import {create} from 'zustand'

export const projectName = create((set) => ({
  state: 0,
    setState: (newState) => set({state: newState})
}))

// ts로 사용할 때.
interface State1 {
  state: number
    setState: (newState: number) => void
}

export const projectName = create<State1>((set) => ({
  state: 0,
    setState: (newState) => set({state: newState})
}))
```
