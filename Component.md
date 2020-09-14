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