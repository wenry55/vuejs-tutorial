# Actions 

액션은 뮤테이션과 비슷합니다. 차이점은,

* 액션은 뮤테이션을 커밋합니다.
* 액션은 임의의 어싱크 오퍼레이션을 포함할 수 있습니다.

간단한 액션의 예는,

```js
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})
```

위의 코드를 좀 더 편하게 하기 위해서는, ES2015의 [argument destructuring](https://github.com/lukehoban/es6features#destructuring)을 이용하여 좀 더 줄일수 있습니다.

```js
actions: {
  increment ({ commit }) {
    commit('increment')
  }
}
```
