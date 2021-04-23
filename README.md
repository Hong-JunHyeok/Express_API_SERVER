# Express로 API 서버를 만드는 방법을 알아봅시다!

![image](https://user-images.githubusercontent.com/48292190/115871562-addff380-a47b-11eb-83c7-d623afbeda53.png)

# 목차
- [시작하기](#시작하기)
- [기본 라우팅](#기본-라우팅)
- [Express에서 정적 파일 제공](#Express에서-정적-파일-제공)

## 시작하기
가장먼저 Hello World를 출력하는 서버를 만들어 볼것이다.
이 예제는 공식문서에도 있는 예제이며, 아마 Express로 프로젝트를 만들때 가장 쉽게 만들수 있는 앱이다.

![image](https://user-images.githubusercontent.com/48292190/115870060-b1727b00-a479-11eb-8d56-2ace2c61d540.png)

위와 같은 명령어로 hello_world라는 폴더를 만들어주고, 그 폴더로 이동해서 작업을 해볼것이다.

이동한 폴더에서 
```
npm init    
```
명령어로 `package.json`을 만들어주자.

`npm init`명령어를 사용하게 되면 몇몇 질의가 주고갈텐데,
공식문서에는 entry point를 index.js로 해도되고 app.js로 해도되고 사용자 마음대로라고 하는 것 같다.
```json
{
  "name": "hello_world",
  "version": "1.0.0",
  "description": "Hello World 예제",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```
이렇게 만든 `package.json`은 이러한 형식일것이다.
이제 본격적으로 `Express`를 설치할 차례이다.

> 공식 문서에는 npm을 사용하지만 나는 yarn이 편하니까 yarn을 사용하도록 하겠다.

```
yarn add express
```
이 작업을 하게 되면, 파일이 여러개 생길텐데, 가장 눈에 띄는것은 
`node_modules`라는 폴더일것이다. 펼쳐보면 정말 많은 폴더들이 있는데, `node_modules`는 npm이나 yarn으로 설치한 라이브러리의 실제 코드가 저장된 곳이다.

이제 `Hello World`를 빌드하기 위한 준비단계는 끝났다. 

이제 `hello_world`폴더 내에 `index.js`를 생성해주자.

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/',(req,res) => {
    res.send("Hello World");
})

app.listen(PORT , () => {
    console.log(`Server is running at ${PORT}`);
})
```
위와 같이 작성을 해주고 
```
node index.js
```
의 작업을 해주게되면, `Server is running at 3000`이라는 문구가 뜨면서 서버가 실행될것이다.

`http://localhost:3000/`로 들어가게 되면 
![image](https://user-images.githubusercontent.com/48292190/115872443-c6044280-a47c-11eb-97c4-aa4f4a390e73.png)

다음과 같이 **잘** 뜰 것이다.

## 기본 라우팅 
라우팅이란? 
> URI(또는 경로) 및 특정한 HTTP 요청 메소드(GET, POST 등)인 특정 엔드포인트에 대한 클라이언트 요청에 애플리케이션이 응답하는 방법을 결정하는 것을 말한다.

```javascript
app.METHOD(PATH, HANDLER)
```
다음과 같은 형식을 가지게되는데, **PATH에는 URI가 들어가게 된다.**
**HANDLER는 라우트가 일치할 때 실행되는 함수이다.**

이제 라우팅 예제를 보면서 익혀보는 시간을 가져보도록 하자.
아까 만든 `hello_world`폴더를 재활용해보자.

```javascript
app.get('/',(req,res) => {
    res.send("Hello World");
})
```
아까 작업했던 코드인데, 이제 어느정도 뭔 역할을 수행하는지 보인다.

- app.get에서 **get**은 GET 메서드를 의미한다.
- '/'부분은 URI 로 /를 받을때를 의미한다.
- (req,res) => {
    res.send("Hello World");
} 부분은 '/'로 라우팅이 됬을때에 실행하는 함수이다.

```javascript
(req,res) => {
    res.send("Hello World");
}
```
여기서 이부분을 조금 자세히 살펴볼건데, 

- req는 리퀘스트이다. 클라이언트측에서 보낸 정보가 담겨있다.

- res는 리스폰스이다. 서버에서 클라이언트로 보낼때의 정보가 담겨있다.

> 이제 어느정도 Express구조가 눈에 보이기 시작한다.

![image](https://user-images.githubusercontent.com/48292190/115874641-475cd480-a47f-11eb-87eb-1c2d9c0fce1a.png)

이렇게 다양한 메서드에 따른 핸들러 함수를 다르게 적용할 수 있다.

## Express에서 정적 파일 제공

> "이미지, CSS 파일 및 JavaScript 파일과 같은 정적 파일을 제공하려면 Express의 기본 제공 미들웨어 함수인 express.static을 사용하십시오. - Express 공식문서"

```javascript
app.use(express.static('public'));
```

위와 같은 형식으로 작성을 하며, 이 코드를 작성하면 public이라는 이름의 디렉토리에 포함된 이미지, CSS 파일 및 JavaScript 파일을 제공한다.

![image](https://user-images.githubusercontent.com/48292190/115877886-e505d300-a482-11eb-8d4a-065493b7b9cb.png)

public뿐만 아니라 여러개의 정적 디렉토리를 지정할 수 있다.

