# Environment

## 학습 가이드

* Node.js
* NPM(Node Package Manager)
  * package.json / package-lock.json
  * node\_modules
  * npx
* ES Modules vs CommonJS

## 개발 환경 세팅

* Node.js
  * Javascript runtime environment that executes Javascript code outside a web browser
  * Built with Chrome V8 JS Engine
  * Sever-Side Rendering 지원
  * 다양한 command line tool 사용 가능
  * backend도 javascript로 개발 가능
  * LTS (Long Term Support)
    * Node version 앞이 홀수 인것은 최신버
* NPM (Node Package Manager)
  * Publish and share course code of Node.js packages
  * simplify installation, updating, and uninstallation of packages
  * 외부 라이브러리를 쉽게 설치하고 버전 관리하도록 지원
  * package.json
    * npm install 시 project root에 생성하는 json 파일
    * 프로젝트 이름, 버전, 사용하는 모든 라이브러리 dependency 명시
  * package-lock.json
  * node\_modules
  * npx
    * bundled with npm 5.2+
    * 라이브러리를 개별적으로 실행할 수 있도록 지원
    * ex) npx \[some-package]
* Deno
  * Node.js와 같은 런타임이다. node의 단어를 앞뒤로 바꿔서 명
  * Node.js 창시자 Ryan Dahl이 Node.js 설계 당시 문제점 지적했고 이를 보완하는 새로운 Runtime
  * Rust 기반으로 구축되어 안전하고 빠른 것이 장
  * 현재 회사 환경과 업무에 사용할 수 없지만 기술적 가치가 있다고 생각
* fnm (fast node manager)
  * [fnm](https://github.com/Schniz/fnm)은 Fast Node Manager의 약어로 Node.js 버전 관리 도구 중 하나
  * fnm은 빠르고 간단한 CLI 도구로, 다양한 Node.js 버전을 쉽게 설치하고 관리할 수 있습니다.&#x20;
  * 제작자가 fnm을 만든 계기는 `nvm`이 너무 느려서.
  * `nvm`에 영향을 받아`nvm`과 비슷한 인터페이스를 가짐
  * `fnm`의 장점은 다음과 같습니다.&#x20;
    * cross-platform 지원
      * nvm은 window를 지원하지 않음 (nvm-windows를 사용해야함)
      * nvm이 window를 지원할 수 없는 이유는 nvm이 bash script이기 때문임
    * nvm에 비해서 속도가 빠름
      * rust로 쓰여져있다.
      * nvm은 bash script임
      * volta와 같이 프로젝트에 진입하면 자동으로 node version 변환 가능&#x20;
      * 설치와 구성이 nvm보다 쉬움

### TypeScript + React + Jest + ESLint + Parcel

* npm 패키지 준비 (y 옵션 설정 시 디폴트로 세팅)

```sh
npm init -y
```

* .gitignore 설정 및 등

```bash
touch .gitignore
```

```gitignore
# dependencies
/node_modules
```

* 타입스크립트 설정

```bash
npm i -D typescript

npx tsc --init
```

* tsconfig.json 설정

```json
{
  "compilerOptions": {
    "baseUrl": "src",
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "types": ["node", "react", "react-dom", "jest", "@testing-library/jest-dom"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "noUnusedParameters": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    // "jsxImportSource": "@emotion/react"
  },
  "include": ["src"],
  "paths": {
    "pages/*": ["pages/*"],
    "containers/*": ["containers/*"],
    "components/*": ["components/*"],
    "sections/*": ["sections/*"],
    "constants/*": ["constants/*"],
    "models/*": ["models/*"],
    "remotes/*": ["remotes/*"],
    "styles/*": ["styles/*"],
    "utils/*": ["utils/*"],
    "hooks/*": ["hooks/*"],
    "stores/*": ["stores/*"]
  }
}

```

* ESLint 설정

```bash
npm i -D eslint

npx eslint --init
```

* .eslintrc.js 수정
  * &#x20;[Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) 같은 널리 알려진 스타일 가이드를 사용하고 싶다면 간단히 [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb) 확장을 설치해서 사용하면 된다.
* .eslintignore 파일 작성

```ignore
node_modules
```

* 리액트 설치

```bash
npm i react react-dom

npm i -D @types/react @types/react-dom
```

* 테스팅 도구 설치

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4
```

* jest.config.js 파일 작성 및 테스트, SWC 사용
* Parcel 설치

```bash
npm i -D parcel
```

* package.json scripts 수정
* 기본 코드 작성

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React App without CRA</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

```jsx
// index.tsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./src/App";

const root = ReactDOM.createRoot(
  document.getElementById("root") as HTMLElement
);
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

```jsx
// App.tsx
import React from "react";

const App = () => (
  <>
    <h1>React without CRA...</h1>
  </>
);

export default App;
```

## TODO

* 세팅해보면 블로그 그룹으로 정리할

<!---->

* [ ] webpack, babel 설정
* [ ] yarn으로 세팅
* [ ] yarn berry로 세팅
* [ ] vite로 세팅

## 참고

* [개발 환경 세팅](https://github.com/ahastudio/til/blob/main/javascript/20181212-setup-javascript-project.md)

