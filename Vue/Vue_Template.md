## [Vue Instance Lifecycle](https://vuejs.org/v2/guide/instance)

***

Vue 인스턴스는 생성될 때 일련의 초기화 과정을 가진다

- 데이터 관찰
- 템플릿 컴파일
- 인스턴스를 Dom에 마운트
- 데이터가 변경되어 Dom을 업데이트
  

![The Vue Instance Lifecycle](https://vuejs.org/images/lifecycle.png)



### Lifecycle Hooks

1. [beforeCreate](https://vuejs.org/v2/api/#beforeCreate): vue 인스턴스가 생성되고  각 정보의 설정 전에 호출 (데이터 접근 x)

2. **[created](https://vuejs.org/v2/api/#created)**: vue 인스턴스가 생성된 후 데이터들의 설정이 완료 후 호출 (데이터 접근 o, 엘리먼트 적용 x)(injections & reactivity)

3. [beforedMount](https://vuejs.org/v2/api/#beforeMount): 마운트가 시작되기 전에 호출 (어떠한 엘리먼트를 쓸지 알고 있음)

4. **[mounted](https://vuejs.org/v2/api/#mounted)**: 지정된 엘리먼트에 vue 인스턴스 데이터가 마운트 된 후에 호출 (Dom 엘리먼트에 Vue가 가지고 있던 속성 값들이 적용됨)

5. [beforeUpdate](https://vuejs.org/v2/api/#beforeUpdate): 지정된 엘리먼트에 vue 인스턴스 데이터가 마운트 된 후에 호출

6. [updated](https://vuejs.org/v2/api/#updated): vue에서 관리되는 데이터가 변경되어 dom이 업데이트 된 상태

7. [beforeDestroy](https://vuejs.org/v2/api/#beforeDestroy): vue instance가 제거되기 전에 호출

8. [destroyed](https://vuejs.org/v2/api/#destroyed): vue instance가 제거된 후에  호출



### Vue Method

Vue 인스턴스는 생성 관련된 데이터 및 메서드의 정의가 가능

메서드 안에서 데이터를 this.데이터이름으로 접근 (this ⇒ Vue인스턴스)

```javascript
new Vue({
            el: "#app",
            data: {
                message: "인사"
            },
            methods: {
                en() {
                    return this.message + ": Hello"
                },
                ko() {
                    return this.message + ": 안녕"
                }
            }
        })
```



### [filters](https://vuejs.org/v2/guide/filters.html)

fliter를 이용하여 표현식에 새로운 결과 형식을 적용

중괄호보간법{{}} 또는 v-bind 속성에서 사용 가능



local filter - 특정한 인스턴스에 국한돼서 사용하고 싶으면 local

```javascript
ilters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
}
```



global filter `- 여러 인스턴스에서 사용하고 싶으면 global

```javascript
Vue.filter('capitalize', function (value) {
  if (!value) return ''
  value = value.toString()
  return value.charAt(0).toUpperCase() + value.slice(1)
})

```



- [computed](https://vuejs.org/v2/api/#computed)

  특정 데이터의 변경사항을 실시간으로 처리할 수 있음

  캐싱을 이용하여 데이터의 변경이 없을 경우 캐싱된 데이터를 반환

  Setter와 Getter을 직접 지정할 수 있음

  작성은 메서드 형태로 작성하지만 Vue에서 프록시 처리하여 프로퍼티처럼 사용

  ```javascript
  var vm = new Vue({
    data: { a: 1 },
    computed: {
      // get only
      aDouble: function () {
        return this.a * 2
      },
      // both get and set
      aPlus: {
        get: function () {
          return this.a + 1
        },
        set: function (v) {
          this.a = v - 1
        }
      }
    }
  })
  console.log(vm)
  // get 메서드 호출
  vm.aPlus   // => 2
  // 값을 설정하기 위해서는 set 메서드 필요함
  vm.aPlus = 3
  vm.a       // => 2
  vm.aDouble // => 4
  ```

  

- [watch](https://vuejs.org/v2/api/?#watch)

Vue 인스턴스의 특정 프로퍼티가 변경될 때 실행할 콜백 함수 설정

**Event**

[v-on](https://vuejs.org/v2/api/#v-on)



Dom 이벤트를 청취하기 위해 v-on 디렉티브 사용

$event 명시적으로 넘겨주기 위함

v-on == @

```javascript
<!-- method handler -->
<button v-on:click="doThis"></button>

<!-- inline statement -->
<button v-on:click="doThat('hello', $event)"></button>

            methods: {
                doThis: function (event) {
                    alert('Hello ' + this.name + '!')
                    console.dir(event.target)
                },
								doThat: function (msg,e) {
                    alert('Hello ' + this.name + '!')
                    console.dir(event.target)
 	                  console.dir(e.target)
                }
            }

<!-- shorthand -->
<button @click="doThis"></button>
```



- [ref](https://vuejs.org/v2/api/#ref)

Vue 인스턴스 객체의 자식 컴포넌트 또는 DOM 엘리먼트 요소

```javascript
<div id="app">
        <h2>엘리먼트 참조하기</h2>

        <!-- 아이디 : <input type="text" v-model="id"> -->
        아이디 : <input type="text" v-model="id" ref="id"> 
        <button @click="check">아이디 중복 체크</button>
    </div>
    <script>
        new Vue({
            el: "#app",
            data: {
                id: ''
            },
            methods: {
                check() {
                    if (this.id.length == 0) {
                        alert("아이디를 입력하세요!!");
                         this.$refs.id.focus();
                         //console.dir(this.$refs.id)
                        return;
                    }
                    alert("아이디 중복체크 성공");
                }
            }
        });
    </script>
```



- [v-bind](https://vuejs.org/v2/api/?#v-bind)

엘리먼트의 클래스와 스타일을 변경

v-bind:class는 조건에 따라서 클래스를 적용할 수 있음

```html
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>

data: {
  isActive: true,
  hasError: false
}
```



- [v-model](https://vuejs.org/v2/api/#v-model)

v-model은 입력 요소에 대해서 특정 속성과 이벤트를 사용함

- v-model은 입력 요소에 대해서 특정 속성과 이벤트를 사용함

  ```html
  <div id="app">
          <div>
              아이디 :
              <input v-model="id" placeholder="아이디를 입력하세요">
              <!-- change 이벤트에 반응 -->
              <input v-model.lazy="id" placeholder="아이디를 입력하세요">
          </div>
          <div>
              메세지 :
              <textarea v-model="message" placeholder="메세지를 입력하세요"></textarea>
          </div>
          <p>{{ id }} 님에게 보내는 메세지 : {{ message }}</p>
  
      </div>
      <script>
          new Vue({
              el: "#app",
              data: {
                  id: "",
                  message: ""
              }
          })
      </script>
  ```

  

- checkbox, radio :checked,change 이벤트 사용

  ```html
  <div id="app">
          <div>
              숫자를 선택하세요
          </div>
          <input type="checkbox" id="1" value="1" v-model="checkedNumber">
          <label for="1">1</label>
          <input type="checkbox" id="2" value="2" v-model="checkedNumber">
          <label for="2">2</label>
          <input type="checkbox" id="3" value="3" v-model="checkedNumber">
          <label for="3">3</label>
          <input type="checkbox" id="4" value="4" v-model="checkedNumber">
          <label for="4">4</label>
          <br>
          <span>체크한 숫자 : {{ checkedNumber }}</span>
      </div>
      <script>
          new Vue({
              el: "#app",
              data: {
                  checkedNumber: []
              }
          })
      </script>
  ```

  

- select : value,change 이벤트 사용

  ```html
  <div id="app">
          <div>
              <p>
                  숫자를 선택하시오
              </p>
              <select v-model="selectedNumber">
                  <option value="">선택하세요</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
              </select>
          </div>
          <span>선택한 숫자 : {{ selectedNumber }}</span>
      </div>
      <script>
          new Vue({
              el: "#app",
              data: {
                  selectedNumber: ""
              }
          })
      </script>
  ```



- checkbox