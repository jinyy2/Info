# ES6

***

## arrow function

function(param){code};

함수 이름이 없는 익명함수이므로 사용시 변수에 담아서 사용

- (param) => {code};   
- param => {code};   # param 1개일 때만
- () => {code};   
- () => code;   # code 한줄 일때만
- () => ({key:value});



## ES6 - Destructuring

객체(배열, 객체)에 입력된 값을 개별적인 변수에 할당하는 간편 방식 제공

```javascript
<script>
    const person = {
      id: 'jinyy2',
      name: 'jin',
      age: 28,
    };
		// ES5
    // let id = person.id;
    // let name = person.name;
    // let age = person.age;
    // console.log(id, name, age);

    // ES6
    let {
      id,
      name,
      age
    } = person;
    console.log(id, name, age);
  </script>
```



```javascript
    <script>
    function getMember() {
      return {
        id: 'jinyy2',
        name: 'jin',
        age: 28,
      };
    }
    let {
      id,
      name,
      age
    } = getMember();
    console.log(id, name, age);
     </script>
```

