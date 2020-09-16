# Component

- Vue의 가장 강력한 기능 중 하나
- HTML 엘리먼트를 확장하여 재사용 가능한 코드를 캡슐화
- Vue 인스턴스의 옵션을 대부분 사용
- 라이프사이플 훅 사용 가능
- 전역 컴포넌트와 지역 컴포넌트



- Local Component

```html
<div id="app1">
        <my-local></my-local>
        <my-local></my-local>
    </div>
    <div id="app2">
        <my-local></my-local>
        <my-local></my-local>
    </div>
    <script>
        new Vue({
            el: "#app1",
            components: {
                MyLocal: {
                    template: '<h2>local componenet</h2>'
                }
            }
        })
        new Vue({
            el: "#app2"
        })
    </script>
```





- Global Component 

````html
<div id="app1">
        <my-global></my-global>
        <my-global></my-global>
    </div>
    <div id="app2">
        <my-global></my-global>
        <my-global></my-global>
    </div>
    <script>
        Vue.component('MyGlobal', {
            template: '<h2>global component</h2>'
        });  
        new Vue({
            el: "#app1"
        })
        new Vue({
            el: "#app2"
        })
    </script>
````



- 컴포넌트 데이터 공유 문제

```html
    <div id="example">
        <simple-counter></simple-counter>
        <simple-counter></simple-counter>
        <simple-counter></simple-counter>
    </div>
    <script>
        var data = { counter: 0 }

        Vue.component('simple-counter', {
        template: '<button v-on:click="counter += 1">{{ counter }}</button>',
        // 데이터는 기술적으로 함수이므로 Vue는 따지지 않지만
        // 각 컴포넌트 인스턴스에 대해 같은 객체 참조를 반환합니다.
        //데이터 공유문제
        data: function () {
            return data
        }
        
        /* 데이터 공유문제 해결
        data: function () {
          return {
            counter: 0
          }
        }
        */
          
        })

        new Vue({
        el: '#example'
        })  
    </script>
```



### 컴포넌트간 통신

부모에서 자식 : props

자식에서 부모 : event

상위 컴포넌트에서 하위 컴포넌트로 데이터 전달

하위 컴포넌트는 상위컴포넌트의 값을 직접 참조 불가능

data와 마찬가지로 props 속성의 값을 템플릿에서 사용이 가능함



객체 props 

객체의 모든 속성을 props로 전달할 경우 인자없이 v-bind를 사용



컴포넌트 객체 데이터 전달



Child -> Parent Event emit

이벤트 발생

vm.$emit();



이벤트 수신

vm.$on();



비 부모 자식간 통신

비어있는 Vue 인스턴스 객체를 이벤트버스로 사용

복잡해질 경우 상태관리 라이브러리 사용 권장(Vuex)



### Module

프로그램을 기능별로 여러 개의 파일로 나누는 형태

- 내보내기 : export default

- 가져오기 : import 모듈명 from 모듈위치