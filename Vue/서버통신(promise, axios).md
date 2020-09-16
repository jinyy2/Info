비동기 처리 - Promis

http xhdtls - axios



## Promise 객체

Promise 객체는 비동기 작업을 마치 동기 작업처럼 값을 봔한해서 사용

형태 

```
new Promise(function (resolve, reject){})
```

resolve(성공시 사용), reject(실패시 사용)



## [Axios](https://github.com/axios/axios)

- Http 통신 

- NodeJs와 브라우저에서 모두 사용할 수 있는 Javascript 라이브러리

- Promise 기반의 HTTP 라이브러리 



***

**Github - Axios features**

- Make [XMLHttpRequests](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) from the browser
- Make [http](http://nodejs.org/api/http.html) requests from node.js
- Supports the [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) API
- Intercept request and response
- Transform request and response data
- Cancel requests
- Automatic transforms for JSON data
- Client side support for protecting against [XSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery)



### GET - 조회

***

```
axios.get(url [, config])
```

```
axios({

method:'get',

url: '/board/10'

});

axios.get('/board/10');
```



### POST - 등록

***

```
axios.post(url [, data, config])
```

```
axios({

method:'post',

url: '/board',

data : {writer: 'jinyy2', title: 'practice'}

});

axios.post('/board',{

	write:'jinyy2',

	title:'practice'

});
```



### PUT - 수정

***

```
axios.put(url [, data, config])
```

```
axios({

method:'put',

url: '/board/10',

data : {writer: 'jinyy2', title: 'practice'}

});

axios.put('/board',{

	write:'jinyy2',

	title:'practice'

});
```



### DELETE - 삭제

***

```
axios.delete(url [, config])
```

```
axios({

method:'delete',

url: '/board/10'

});

axios.delete('/board/10');
```





사용 예제)

```javascript
    new Vue({
      el: "#app",
      data: {
        storeList: []
      },
      created() {
        axios.get(url)
          .then((response) => {
            this.storeList = response.data.stores
          }).catch((error) => {
            console.dir(error);
          });
      }
    })
```







