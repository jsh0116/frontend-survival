# Express

Express : Node.js 서버 프레임워크

> [Express](https://expressjs.com/ko/)

**간단한 서버 앱 npm 패키지 세팅**

> [Express 설치](https://expressjs.com/ko/starter/installing.html)
>
> [ts-node](https://github.com/TypeStrong/ts-node)

* 프로젝트 생성

```bash
mkdir express-demo-app
cd mkdir express-demo-app
touch .gitignore
echo "/node_modules/" > .gitignore
```

* 프로젝트 초기화 (package.json, typescript, eslint)

```bash
npm init -y
npm i -D typescript
npx tsc --init
npm i -D ts-node
npm i -D eslint
npx eslint --init
```

* express 설치 (typescript)

```
npm i express
npm i -D @types/express
```



**Hello World 예제**

> [Express 예제](https://expressjs.com/ko/starter/hello-world.html)

```javascript
import express from 'express';

const port = 3000;

const app = express();

app.get('/', (req, res) => {
  res.send('Hello, world!');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

* ts-node를 통해 실행

```bash
npx ts-node app.ts
```

* &#x20;[nodemon](https://github.com/remy/nodemon) 사용 : 코드를 수정할 때마다 서버를 재실행할 필요 없음

```bash
npm i -D nodemon
npx nodemon app.ts
```
