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



v-: directive

- v-once: 데이터 변경 시 업데이트 되지 않는 일회성 보간 수행

- v-text, {{속성명}}  : 데이터 속성의 html을 escape 처리

- v-html : 데이터 속성의 html을 파싱하여 처리

```javascript
<div>메세지: {{msg}}</div>
<div v-text="'메세지: ' + msg">무시된다.</div>
<div v-html="'메세지: ' + msg">무시된다.</div>

메세지: <h2>Hello Vue~</h2>
메세지: <h2>Hello Vue~</h2>
메세지: Hello Vue~(html적용)
  
data: {
  msg: "<h2>Hello Vue~</h2>"
}
```

