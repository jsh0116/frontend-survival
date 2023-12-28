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
    * 컴포넌트도 OOP-SOLID 중 SRP 원칙을 지켜야 한다.
    * 이를 지키지 않으면 컴포넌트에 자바스크립트 로직이 방대해지고 조건에 따라 렌더링이 많아질 것이다.
    * 실제로 이를 지키지 않아 현업에서 매우 개발이 어려운적이 있었다. 아무리 커뮤니케이션 시도해도 담당 팀에서 코드가 방대해져 유지보수하기 힘들다는 식으로 미루게 된다.
    * 컴포넌트 분리할때 CSS classname도 작성도 고려해야한다.
    * component hierarchy는 디자인 계층을 나누는 것과 가깝다고도 할 수 있다.
    * JSON Schema 구조를 프론트에서 가공하여 적절히 뿌리고 컴포넌트에서 각각 표현해주는 것도 중요하다.
  * DOM Tree 구축하듯이 Component Tree를 구축하는 것
    * SPA에서 페이지 구성요소를 컴포넌트화 해서 캡슐화 및 재사용성을 극대화 시키고 복잡한 UI를 레고 쌓듯이 만들고 트리 형태로 구성하면 대략적으로 페이지의 구성 요소를 적절히 보여줄 수 있다.
* Step 2: Build a static version in React
  *   step1을 고려하여 top-down 방식 혹은 bottom-up 방식으로 컴포넌트를 구현하면 된다.&#x20;



## Data

## Component 계층 구조

## Extract Function

## Props

## Reference
