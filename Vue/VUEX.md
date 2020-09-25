# [VUEX](https://vuex.vuejs.org/kr/)

***

- vue.js 애플리케이션에 대한 상태관리패턴 + 라이브러리
- 애플리케이션 모든 컴포넌트들의 중앙 저장소 역할(데이터 관리)
- 부모 자식 관계가 많이 복잡해진다면 데이터의 전달하는 부분이 매우 복잡해짐
- 애플리케이션이 여러 구성요소로 구성되고 더 커지는 경우 데이터 공유하는 문제가 발생



### 상태 관리 패턴

단방향 데이터 흐름

![image-20200920152608166](/Users/jinyy2/Library/Application Support/typora-user-images/image-20200920152608166.png)

```
new Vue({
  // 상태
  data () {
    return {
      count: 0
    }
  },
  // 뷰
  template: `
    <div>{{ count }}</div>
  `,
  // 액션
  methods: {
    increment () {
      this.count++
    }
  }
})
```





### Vuex 핵심 컨셉

![image-20200920153335623](/Users/jinyy2/Library/Application Support/typora-user-images/image-20200920153335623.png)

Actions : 비동기 처리에 적합

Mutations : 동기 처리에 적합



**CDN** 

```
<script src="https://unpkg.com/vuex"></script>
```



**NPM**

```
npm install vuex --save
```





### Vuex 저장소 개념

`State` : 단일 상태 트리 사용, 애플리케이션마다 하나의 저장소를 관리(data)

`Getters` : Vue 인스턴스의 Computed 같은 역할, State를 기반으로 계산(computed)

`Mutations` : State의 상태를 변경하는 유일한 방법(methods)

`Actions` : 상태를 변이시키는 대신 액션으로 변이에 대한 커밋 처리(비동기 methods) 





### Vuex 사용

store/index.js

```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex) -> Vue 객체에 Vuex를 설정

export default new Vuex.Store({
  state: {
  },
  mutations: {
  },
  actions: {
  },
  modules: {
  }
})
```



main.js 

```
import store from './store'

new Vue({
  store,
  render: h => h(App)
}).$mount('#app')
```



저장소(Store) - State

- 저장소에서 data 속성의 역할
- 애플리케이션에서 공유해야 할 데이터를 관리
- State에 접근하는 방식
  this.$store.state.데이터이름



### 저장소 - Getters

컴포넌트가 Vuex의 state를 직접 접근하는 코드가 중복된다면?

Store의 state를 참조하는 Getters를 활용

정의

getters:{

​	countMsge(state){

​	state.count += 1;

}

}

사용 : this.$store.getters.countMsg



### 저장소 - Mutations

- State의 값을 변경하기 위해서 사용

- 각 컴포넌트에서 State의 값을 직접 변경하는 것은 권장하지 않는 방식

- State의 값의 추적을 위해 동기적 기능에 사용

- Mutations는 직접 호출이 불가능하고 store.commit('정의된 이름')으로 호출



사용: this.$store.commit('')



### 장소 - Actions

- 비동기 작업의 결과를 적용하려고 할 때 사용
- Mutations는 상태 관리를 위해 동기적으로 처리하고 비동기적인 처리는 Actions가 담당
- Actions는 비동기 로직의 처리가 종료 되면 Mutations를 호출



store에서 부르지 않음

사용: this.$store.dispatch('');