# State


### Single State Tree

Vuex 는 single state tree 를 사용합니다. 말인 즉슨, "single source of truth", 즉 한개의 공용저장소를 사용한다는 의미입니다. 트리라는 말이 붙은것은 루트아래 프라퍼티들이 달려있는 집합체를 표현합니다.

### Vue 컴포넌트에서 사용하기


```js
// let's create a Counter component
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return store.state.count
    }
  }
}
```

Vue 컴포넌트에서는 위와 같이 사용합니다. computed를 이용해서 값을 읽어와서 표현하는 데 사용합니다.

하지만 위의 패턴대로는 약간 사용하기 힘들 수 있는데, 위와 같이 쓰려면 모든 컴포넌트에서 store를 import 해야하기 때문입니다. 



### <span style='color:red;font-weight:bold'>*mapState*</span> 헬퍼


state store 오브젝트에 접근해서 사용해야 할 computed 필드가 많은 경우, 이를 좀 편하게 하는 방법이 있습니다. mapState 함수를 이용하여 computed 함수 리스트를 가져올 수 있습니다.

```js
// in full builds helpers are exposed as Vuex.mapState
import { mapState } from 'vuex'

export default {
  // ...
  computed: mapState({
    // arrow functions can make the code very succinct!
    count: state => state.count,

    // passing the string value 'count' is same as `state => state.count`
    countAlias: 'count',

    // to access local state with `this`, a normal function must be used
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}
```
