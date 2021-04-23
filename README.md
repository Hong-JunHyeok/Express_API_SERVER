# Express의 공식문서를 보고 만들어보는 API 서버입니다.

![image](https://user-images.githubusercontent.com/48292190/115871562-addff380-a47b-11eb-83c7-d623afbeda53.png)

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