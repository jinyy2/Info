## vue-router

***

- 라우팅 - 웹페이지간의 이동방법

- vue.js의 공식 라우터

- 라우터는 컴포넌트와 매핑

- Vue를 이용한 SPA를 제작할 때 유용

- url에 따라 컴포넌트를 연결하고 설정된 컴포넌트를 보여준다.



**CDN**

```html
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```



NPM

```
npm install vue-router
```



`routes` 옵션과 함께 router 인스턴스 생성

```
const router = new VueRouter({

	routes:[

	{path:'/', component: Main},

	{path:'/login', component: Login}

]

});
```



### vue-router 이동 및 렌더링

- 네비게이션을 위해 router-link 컴퓨넌트를 사용

- 속성은 to prop을 이용

- 기본적으로 `<router-link>`는 `<a>`태그로 렌더링

  <router-link to ="/"> 메인페이지 이동</router-link>

- 현재 라우트에 맞는 컴포넌트가 렌더링

  <router-view></router-view>

  

### $router, $route

라우터 설정

```
{

path:'/board/:no',

component:BoardView,

}
```



라우터 링크

<router-link to="/board/2">2번 게시글</router-link>



`BoardView`

```
data() {
	return {no: 0,};
	},

create(){

console.log(this.$router); //전체 라우터 정보

console.log(this.$route); //현재 라우터 정보

this.no = this.$route.params.no;

}
```



### 이름을 가지는 라우트

라우트에 연결하거나 탐색을 수행할 때 이름이 있는 라우트를 사용

Router 인스턴스를 생성하는 동안 routes 옵션에 지정

```
{

path:'/board/:no',
name: 'boardview',
component:BoardView,

}
<router-link:to="{name: 'boardview',params:{no:2}}"
```





### 프로그래밍 방식 라우터

<router-link>를 사용하여 선언적 네비게이션용 anchor 태그를 만드는 것 외에도 라우터의 인스턴스 메소드를 사용하여 프로그래밍으로 수행

$router.push('home'); // path

$router.push({path: 'home'}); // path

$router.push({name:'user',params:{userId:123}});

$router.push({path:'register', query: {userId: '123'}) // ?userId=123





### 중첩된 라우트

앱 UI는 일반적으로 여러 단계로 중첩된 컴포넌트 구조임

URL의 세그먼트가 중첩된 컴포넌트의 특정 구조와 일치하는 것을 활용

/board/list

/board/write



```
{
path:'/board',
component:Board,
children:[
{path:list,
component:BoardList},
{path:write,
component:BoardWrite},
]
}
```

