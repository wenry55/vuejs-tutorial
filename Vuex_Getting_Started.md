
먼저, 아래와 같이 선언하여 store라는 state 오브젝트를 사용하도록 합니다.


```javascript
// Make sure to call Vue.use(Vuex) first if using a module system

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```



위와 같이 한 뒤, 변경을 가할 경우, 

```js
store.commit('increment')

console.log(store.state.count) // -> 1
```

와 같이 변경할 수 있습니다. 여기에서 값을 바꿀 때 일반적인 방법과 다른것을 알 수 있는데, 이렇게 하는 이유는 스테이트의 변경을 명시적으로 표기함으로써, 코드를 읽을때 스테이트가 변경된다는 것을 인지 할 수 있게 하기 위함입니다. 그리고, 스테이트가 변경될 때 이를 로깅할 수 있는 것과 같은 여지를 남겨두기 위함입니다. 

컴포넌트에서 store state를 사용하는 방법은 computed property에서 state를 리턴하는 것이 가장 쉬운방법입니다. 

[다음](./Vuex_Core_Concepts_State.md)