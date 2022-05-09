# Redux

>Redux Toolkit을 이용한 Redux 사용법

### 1. Store 생성하기

`src/redux/store.js`

```react
import { configureStore } from '@reduxjs/toolkit'

export default configureStore({
    reducer: {}
})
```

`configureStore`를 사용하여 빈 Redux store를 생성한다.



### 2. Store를 React에 제공하기

`src/index.js`

```react
import React from 'react'
import ReactDOM from 'react-dom'
import './index.css'
import App from './App'
import store from './redux/store'
import { Provider } from 'react-redux'

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

React에서 Store를 이용할 수 있게 `<App>`을 `<Provider>`로 감싸준다.



### 3. Redux State Slice 생성하기

`src/features/counter/counterSlice.js` 

>**naming convention**
>
>- slice이름 + Slice
>
>- camelCase로 작성

```react
import { createSlice } from '@reduxjs/toolkit'

export const counterSlice = createSlice({
  name: 'counter',
  initialState: {
    value: 0
  },
  reducers: {
    increment: state => {
      state.value += 1
    },
    decrement: state => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    }
  }
})

// Action creators are generated for each case reducer function
export const { increment, decrement, incrementByAmount } = counterSlice.actions

export default counterSlice.reducer
```

`createSlice`를 이용하여 Slice를 만들고 name, initial state 값, reducer 함수를 정의한다.

slice를 정의한 후 action creators, reducer function을 export한다.



### 4. Store에 Slice Reducers를 추가하기

`src/redux/store.js`

```react
import { configureStore } from '@reduxjs/toolkit'
import counterReducer from '../features/counter/counterSlice'

export default configureStore({
  reducer: {
    counter: counterReducer
  }
})
```

state를 update하기 위해 slice reducer function을 사용하겠다고 말하는 과정이다.



### 5. React Component에서 Redux State, Action 사용하기

`src/feature/counter/Counter.js`

```react
import React from 'react'
import { useSelector, useDispatch } from 'react-redux'
import { decrement, increment } from './counterSlice'
import styles from './Counter.module.css'

export function Counter() {
  const count = useSelector(state => state.counter.value)
  const dispatch = useDispatch()

  return (
    <div>
      <div>
        <button
          aria-label="Increment value"
          onClick={() => dispatch(increment())}
        >
          Increment
        </button>
        <span>{count}</span>
        <button
          aria-label="Decrement value"
          onClick={() => dispatch(decrement())}
        >
          Decrement
        </button>
      </div>
    </div>
  )
}
```

`<Counter>` component를 생성한다.

`useSelector`로 Redux State 데이터를 가져올 수 있다.

`userDispatch`로 Redux Action을 사용할 수 있다.



참고: [redux quick-start](https://redux.js.org/tutorials/quick-start)

