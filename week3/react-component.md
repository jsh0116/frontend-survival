# React Component

* REST API 와 GraphQL
  * REST API 란 무엇인가
  * GraphQL은 왜 등장했는가?
  * REST API vs GraphQL
* JSON
* DSL(Domain-Specific Language)
* 선언형 프로그래밍
* 명령형 프로그래밍
* SRP(단일 책임 원칙)
* Atomic Design
* React component 와 props

## [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)

* Step 1: Break the UI into a component hierarchy&#x20;
  * UI를 컴포넌트 계층별로 쪼개는것
  * DOM Tree 구축하듯이 Component Tree를 구축하는 것
    * SPA에서 페이지 구성요소를 컴포넌트화 해서 캡슐화 및 재사용성을 극대화 시키고 복잡한 UI를 레고 쌓듯이 만들고 트리 형태로 구성하면 대략적으로 페이지의 구성 요소를 적절히 보여줄 수 있다.
* Step 2: Build a static version in React
  * step1을 고려하여 top-down 방식 혹은 bottom-up 방식으로 컴포넌트를 구현하면 된다.&#x20;

## Data

결국 FE에서는는 BE로부터 응답받는 JSON Data를 표현하는 것이고 이를 위해 BE에서 API를 제공한다. 방식은 REST API(대부분 사용) or GraphQL

* REST API
  * REST란 Representational State Transfer의 약자
  * 자원을 정의하고 자원에 대한 주소를 지정하는 네트워크 아키택처 모음
  * Resource의 표현(Representation)에 의한 상태 전달
  * 구성 요소
    * Resource - URI
      * 모든 리소스에는 고유한 아이디가 존재하고 이 자원은 서버에 존재한다
      * 자원을 구별하는 ID는 HTTP URI이다
      * 클라이언트는 URI를 이용해서 자원을 지정하고 해당 자원의 상태에 대한 조작을 서버에 요청한다.
    * Verb - HTTP Method (GET, POST, PUT, PATCH, DELETE)
    *   Representation

        * 클라이언트가 리소스에 대한 조작을 요청하면 서버는 이에 대해 응답
        * 리소스는 JSON, XML 등으로 표현되어 나타낼 수 있다.


* GraphQL
  * Graph 자료 구조를 이용
  * Query에서 얻고자 하는 걸 Schema 처럼 지정해준다
    * ex) Post만 얻을 것인지, Post에 딸려있는 Comment까지 얻을 것인지 쿼리에서 결정해준다.
  * Query(Read)
  * Mutation(Command: Create, Update, Delete)
  * Subscription(Event를 인지하는 용도): 쿼리에 대해서 인지를 하지는 않는다. Mutation에 대해서 인지를 한다.
  * 주로 Query와 Mutation이 중심이 된다.

## Component 계층 구조

* React의 강력한 특징
  * Declarative
  * Component-Based
  * Build encapsulated components that manage their own state, then compose them to make complex UIs
  * 사실 리액트 뿐만 아니라 다른 FE Framework도 포함하는 특징들이다.
* 컴포넌트를 나누는 기준들
  * [SRP](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%B1%85%EC%9E%84\_%EC%9B%90%EC%B9%99)
    * 컴포넌트도 OOP-SOLID 중 SRP 원칙을 지켜야 한다.
    * 이를 지키지 않으면 컴포넌트에 자바스크립트 로직이 방대해지고 조건에 따라 렌더링이 많아질 것이다.
    * 실제로 이를 지키지 않아 현업에서 매우 개발이 어려운적이 있었다. 아무리 커뮤니케이션 시도해도 담당 팀에서 코드가 방대해져 유지보수하기 힘들다는 식으로 미루게 된다.
  * CSS
    * 컴포넌트 분리할때 CSS classname도 작성도 고려해야한다.
    * css를 만들어야겠다고 생각할 때 우리는 머리속으로 컴포넌트를 쪼갠다.
  * Design's Layer
    * component hierarchy는 디자인 계층을 나누는 것과 가깝다고도 할 수 있다.
    * 최근엔 [Atomic Design Pattern](https://bradfrost.com/blog/post/atomic-web-design/)을 적극적으로 도입하여 UI상에서 Layer를 나누고 컴포넌트 재사용성을 극대화하려고 한다.
  * Info Architecture
    * JSON Schema 구조를 프론트에서 가공하여 적절히 뿌리고 컴포넌트에서 각각 표현해주는 것도 중요하다.
    * JSON 구조를 그대로 보여주기에 조금 애매하다면 프론트 단에서 가공을 해서 화면에 뿌려줄 수도 있고, 백엔드에 요청해서 데이터를 변환해달라고 할 수도 있다.
    * 만약 데이터 구조가 좋지 않으면 백엔드에서 수정하는 편이 좋다 (서버의 확장성을 생각했을때)

## Extract Function

> [Extract Function](https://refactoring.com/catalog/extractFunction.html)
>
> [Inline Function](https://refactoring.com/catalog/inlineFunction.html)

공통 로직들은 함수로 추출해놓을 것. (리팩토링 책에 나와있다.)

## Props

> [Passing Props to a Component](https://beta.reactjs.org/learn/passing-props-to-a-component)
>
> [Components와 Props](https://ko.reactjs.org/docs/components-and-props.html)

* 단방향 데이터 바인딩을 지원하는 리액트에서 부모 → 자식 컴포넌트로 내려주는 읽기 전용 데이터
* 나눠진 컴포넌트를 서로 연결하는 방법 중 하나
* TypeScript를 잘 쓰거나 잘못 쓰게 되는 포인트 중 하나. 적절한 균형점을 잡는 게 중요
* 테스트 코드를 작성하면 재사용성을 평가하기 쉬워짐.

## Reference

* [https://fe-developers.kakaoent.com/2022/220505-how-page-part-use-atomic-design-system/](https://fe-developers.kakaoent.com/2022/220505-how-page-part-use-atomic-design-system/)
* [https://react.dev/learn/sharing-state-between-components#step-2-pass-hardcoded-data-from-the-common-parent](https://react.dev/learn/sharing-state-between-components#step-2-pass-hardcoded-data-from-the-common-parent)
