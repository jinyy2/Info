# [VUE](https://vuejs.org/)

### MVVM 패턴

Model, View, ViewmModel

![MVVMPattern.png](https://upload.wikimedia.org/wikipedia/commons/8/87/MVVMPattern.png)



### Vue 설치 방법

https://kr.vuejs.org/v2/guide/installation.html

#### CDN

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```



### Vue 인스턴스

https://kr.vuejs.org/v2/guide/instance.html

모든 Vue 앱은 Vue 함수로 새 Vue 인스턴스를 만드는 것부터 시작한다.

Vue 앱은 new Vue를 통해 만들어진 루트 Vue 인스턴스로 구성되며 선택적으로 중첩이 가능하고 재사용 가능한 컴포넌트 트리로 구성됩니다.

```js
var vm = new Vue({
  // 옵션
})
```



el: "css 선택자" or HTML Element, Vue가 적용될 요소 지정

```js
<div id="app"></div>

new Vue({
	el:"#app"
});
```



data: 객체 or 함수, Vue에서 사용되는 정보를 저장

```js
<div id="app">
	<h2>{{msg}}</h2>
</div>

new Vue({
	el:"#app",
	data:{
	msg:'Hello'	
	}
});
```



## v-: directive

- v-once: 데이터 변경 시 업데이트 되지 않는 일회성 보간 수행

- [v-text](https://vuejs.org/v2/api/#v-text), {{속성명}}  : 데이터 속성의 html을 escape 처리

- [v-html](https://vuejs.org/v2/api/#v-html) : 데이터 속성의 html을 파싱하여 처리

```javascript
<div>메tl지: {{msg}}</div>
<div v-text="'메시지: ' + msg">무시된다.</div>
<div v-html="'메시지: ' + msg">무시된다.</div>

메시지: <h2>Hello Vue~</h2>
메시지: <h2>Hello Vue~</h2>
메시지: Hello Vue~(html적용)
  
data: {
  msg: "<h2>Hello Vue~</h2>"
}
```



- [v-model](https://vuejs.org/v2/api/#v-model): 양방향 바인딩 처리를 위해서 사용( 폼의 **input, textarea** )

  v-model="msg" : msg가 단순한 문자열이 아니게 됨
  
- [v-bind](https://vuejs.org/v2/api/#v-bind): 엘리먼트 속성 바인딩 처리를 위해서 사용
  v-bind:속성명   ⇒ ' : ' 약어로 쓸 수 있다.


- [v-show](https://vuejs.org/v2/api/#v-show): 조건에 따라 엘리먼트를 화면에 표시

  style 속성의 display를 변경

- [v-if](https://vuejs.org/v2/api/#v-if)

- [v-else-if](https://vuejs.org/v2/api/#v-else-if)

- [v-else](https://vuejs.org/v2/api/#v-else)

  조건에 맞는 경우 화면에 요소들을 랜더링

  ```HTML
          <div>
              <span>나이 : </span>
              <input type="number" v-model="age">
          </div>
          <div>
              요금 :
              <span v-if="age < 10">무료</span>
              <span v-else-if="age < 20">7000원</span>
              <span v-else-if="age < 65">10000원</span>
              <span v-else>3000원</span>
          </div>
  ```

  

- [v-for](https://vuejs.org/v2/api/#v-for) : 배열이나 객체의 반복에 사용

  v-for="요소변수 이름 in 배열"

  v-for="(요소변수이름,인덱스) in 배열"

  ```HTML
  <div v-for="item in items">
    {{ item.text }}
  </div>
  ```
  
  
  
- [template](https://vuejs.org/v2/guide/conditional.html#Conditional-Groups-with-v-if-on-lt-template-gt): 여러개의 태그들을 묶어서 처리해야한다면 template를 이용하면 편리

  v-if, v-for, component 등과 함께 많이 사용

```html
<template v-for="item in items">
            <h2>{{ item.text }}</h2>
            <h3>{{ item.text }}</h3>
        </template>
```



- [v-cloak](https://vuejs.org/v2/api/#v-cloak): Vue인스턴스가 준비될 때까지 mustache 바인딩을 숨기는데 사용

