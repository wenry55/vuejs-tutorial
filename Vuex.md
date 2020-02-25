# Vuex


Vuex는 state management pattern + library 를 말합니다.
이는 한 어플리케이션내의 모든 컴포넌트들을 위한 중앙화된 저장소 역할을 합니다.

What is a "State Management Pattern"? 

먼저 State Management Pattern이 무엇을 말하는지 살펴보겠습니다.

![State Management  Pattern](https://vuex.vuejs.org/flow.png)

* State, The source of truth.
* View, a declarative mapping of the state
* Action, the possible ways of the state could change in reaction to user inputs from the view.

위의 패턴은 여러개의 컴포넌트가 한개의 state를 공유하게 될 때 브레이크 됩니다.
(multiple components that share a common state)

Read [Getting Started](./Vuex_Getting_Started.md)




### 언제 사용하는 것이 좋을까?

현재 CDMS 상에서 사용하고 있는 랙 정보를 보여주는 컴포넌트들에서 한개의 랙정보를 서로 다른 컴포넌트들로 렌더링하는 부분에서 사용할 수 있겠다.
