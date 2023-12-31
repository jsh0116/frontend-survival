# JSX

## 학습가이드

* React에서 JSX를 사용하는 목적
* Syntax sugar
* React.createElement
* React Element
* React StrictMode
* VDOM(Virtual DOM)이란?
  * DOM이란?
  * DOM과 Virtual DOM의 차이
* Reconciliation(재조정) 과정은 무엇인가?

## 강의 내용

### JSX

* XML-like syntax extension to ECMAScript
* 별도의 파일에 마크업과 자바스크립트 로직을 포함하는 컴포넌트로 구현
  * Loosely coupled한 상태로 관심사의 분리 적ㅇㅇ
* React에서는 JSX 문법으로 작성된 코드를 해석하고 실행할 때 React Element로 변환해서 사용
* 장점
  * HTML 문법을 알고있다면 UI 작업 시 더 직관적으로 코드를 이해할 수 있다.
  * 리액트는 마크업 파일과 여러가지 로직을 담고 있는 파일을 분리하지 않고 컴포넌트라는 개념으로 하나의 파일에 코드를 작성 → 높은 응집도
  * 느슨한 연결을 통해 관심사 분리 가능 → UI 부분과 상태를 변경하는 렌더링 로직 분리 가능
* 어떻게 동작하는가?
  * 리액트 라이브러리인 createElement를 Syntax Sugar한 개념 (문법은 그대로인데 직관적으로 이해가 가능한 코드를 만드는 것)
  * JSX 문법이 적용된 코드는 babel을 통해 React.createElement라는 함수 호출로 변경된다
* 사용시 주의점
  * Component 이름은 반드시 대문자여야 한다
    * 소문자로 시작하는 Element는 내장 컴포넌트로 인식하게 된다.
    * 내장 컴포넌트는 createElement에서 ‘div’나 ‘span’ 같은 문자열 형태로 전달하고 처리하므로 문제 발생할 수 있다.
  * class(HTML Element 속성) 대신 className 사용

### Example1

* JSX 코드

```html
<p>Hello, world!</p>
```

* 변환된 JSX 코드

```jsx
React.createElement("p", null, "Hello, world!");
```

### Example2

* JSX 코드

```html
<Greeting name="world" />
```

* 변환된 JSX 코드

```jsx
React.createElement(Greeting, { name: "world" });
```

### Example3

* JSX 코드

```html
<Button type="submit">Send</Button>
```

* 변환된 JSX 코드

```jsx
React.createElement(Button, { type: "submit" }, "Send");
```

### Example4

* JSX 코드

```html
<div className="test">
    <p>Hello, world!</p>
    <Button type="submit">Send</Button>
</div>
```

* 변환된 JSX 코드

```jsx
React.createElement(
    "div",
    { className: "test" },
    React.createElement("p", null, "Hello, world!"),
    React.createElement(Button, { type: "submit" }, "Send")
);
```

### Example5

* JSX 코드

```html
<div>
    <p>Count: {count}!</p>
    <button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>
```

* 변환된 JSX 코드

```jsx
React.createElement(
    "div",
    null,
    React.createElement("p", null, "Count: ", count, "!"),
    React.createElement("button", { type: "button", onClick: () => setCount(count + 1) }, "Increase")
);
```

## React Element

* `type`과 `props`를 가지는 객체
* React.createElement를 이용하여 만들 수 있고 type으로 HTML  Tag 이름을 가지고 그 이외의 특징을 props로 관리
* JSX없이도 React를 사용할 수 있다, JSX로 할 수 있는 모든 것은 순수 JavaScript로도 할 수 있지만 JSX로 리액트 어플리케이션을 작성하는 것이 가독성, 생산성 측면에서 모두 좋다고 생각한다.

## Virtual DOM

* 사용하는 이유
  * js를 통해 화면을 나타내는 DOM을 수정하면 rendering 과정 중 레이아웃이나 페인트 과정이 다시 발생하게 된다
  * 반응형 웹에서 이런 수정이 많이 발생하게 되면 특히 리플로우 과정이 많이 발생하면 브라우저 성능이 악화
  * 그래서 리액트는 가상 돔에 변경 사항을 적용하고 실제로 변경된 부분을 계산해서 돔에 일괄적으로 적용하는 Batch Update를 적용해서 성눙을 최적화
* 동작 방식
  * React는 Reconciliation 과정을 통해 Virtual DOM을 이용해서 실제 돔 조작
    * Reconciliation: 데이터 변경에 따라 어떤 컴포넌트가 변경되어야 하는지 선별하여 갱신하는 작업
  * 리액트는 항상 2개의 가상 돔을 가지고 있음 (업데이트를 위한, 업데이트가 되지 않은)
  * diffing 알고리즘을 통해 비교
  * 알고리즘 결과로 실제 변경된 부분을 알 수 있고 그 부분을 일괄적으로 실제 DOM에 적용
  * fiber : 리액트 가상 돔 변경과정에서 발생하는 동시성, 애니메이션과 같은 문제점들을 해결하기 위해 적용한 알고리즘
* [VDOM (Virtual DOM)](https://ko.reactjs.org/docs/faq-internals.html)
* [재조정 (Reconciliation)](https://ko.reactjs.org/docs/reconciliation.html)

### React Developer Tools

* [react devtools extensions](https://github.com/facebook/react/tree/main/packages/react-devtools-extensions)
  * [Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)를 쓰지 않으면 경고함.

## References

* [facebook의 JSX 소개](https://facebook.github.io/jsx/)
* [React 공식문서의 JSX 소개](https://ko.reactjs.org/docs/introducing-jsx.html)
* [Babel, JSX, 그리고 빌드 과정들](https://ko.reactjs.org/docs/faq-build.html)
* [JSX 이해하기](https://ko.reactjs.org/docs/jsx-in-depth.html)
