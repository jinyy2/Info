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

  