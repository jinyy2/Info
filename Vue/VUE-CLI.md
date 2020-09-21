

## Vue-CLI 환경 구축 및 프로젝트 생성

***

[NodeJS 설치](https://nodejs.org/ko/) - LTS 버전(NPM 같이 설치됨)

NPMdmf dldydgks Vue-CLI 환경 설치



**NPM(Node Package Manager)**

Command에서 써드파티 모듈을 설치하고 관리하는 툴



[패키지 검색](https://www.npmjs.com)

npm init : 새로운 프로젝트나 패키지를 만들 때 사용(package.json이 생성)

`package.json`

```
package name: (work_vue)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to /Users/jinyy2/ssafy/work_vue/package.json:

{
  "name": "work_vue",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

npm install package : 생성되는 위치에서만 사용 가능한 패키지로 설치

npm install -g package : 글로벌 패키지에 추가, 모든 프로젝트에서 사용 가능한 패키지로 설치



### [VUE-CLI](https://cli.vuejs.org/)

- CLI - Command Line Interface(명령줄 인터페이스)

- Vue.js 개발을 위한 시스템으로 Vue.js에서 공식으로 제공하는 CLI

- 개발의 필수는 아니지만 개발의 편리성을 위해 필수처럼 사용

- Vue 프로젝트를 빠르게 구성할 수 있는 스캐폴딩을 제공

- Vue와 관련된 오픈 소스들의 대부분이 CLI를 통해 구성이 가능하도록 구현



```
npm install -g @vue/cli
npm install -g -force @vue/cli
vue -version or vue -V
```





vue init [webpack-simple]



#### 바벨(BabelJS)

ECMA2015 이상의 문법을 ES5의 자바스크립트 코드로 변경하는 도구 

자바스크립트 컴파일러



#### 웹팩(Webpack)

웹팩은 오픈 소스 자바스크립트 모듈 번들러이다. 주로 자바스크립트(JS)를 위한 모듈 번들러이지만 호환 플러그인을 포함하는 경우 HTML, CSS, 심지어는 이미지와 같은 프론트엔드 자산들을 변환할 수 있다. 웹팩은 의존성이 있는 모듈을 취하여 해당 모듈을 대표하는 정적 자산들을 생성한다.



![image-20200917030155856](/Users/jinyy2/Library/Application Support/typora-user-images/image-20200917030155856.png)



``` 
npm run build
```





```
vue create vue_board
```

? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, Router, Linter
? Use history mode for router? (Requires proper server setup for index fallback
in production) Yes
? Pick a linter / formatter config: Prettier
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated confi
g files
? Save this as a preset for future projects? (y/N) N



**프로젝트 실행** 

```
npm run serve
```

